---
title: Completar requisitos previos
description: Prepare su proyecto de Adobe Commerce para una actualización completando estos pasos previos.
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: df185e21f918d32ed5033f5db89815b5fc98074f
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 0%

---

# Completar requisitos previos de actualización

Es importante comprender lo necesario para ejecutar Adobe Commerce. Primero debe revisar los [requisitos del sistema](../../installation/system-requirements.md) para la versión a la que planea actualizar.

Después de revisar los requisitos del sistema, debe completar los siguientes requisitos previos antes de actualizar el sistema:

* Actualizar todo el software
* Compruebe que haya instalado un motor de búsqueda compatible
* Convertir formato de tabla de base de datos
* Establecer el límite de archivos abiertos
* Verificar que los trabajos cron se estén ejecutando
* Establecer `DATA_CONVERTER_BATCH_SIZE`
* Comprobar permisos del sistema de archivos
* Establecer la raíz del directorio `pub/`
* Instalación del complemento de actualización del Compositor

## Actualizar todo el software

Los [requisitos del sistema](../../installation/system-requirements.md) describen exactamente qué versiones de software de terceros se han probado con las versiones de Adobe Commerce.

Asegúrese de haber actualizado todos los requisitos y dependencias del sistema de su entorno. Consulte PHP [7.4](https://www.php.net/manual/en/migration74.php), PHP [8.0](https://www.php.net/manual/en/migration80.php), PHP [8.1](https://www.php.net/manual/en/migration81.php) y [configuración de PHP requerida](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>Para los proyectos Pro de Adobe Commerce en la nube, debe crear un ticket de [Soporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=es#submit-ticket) para instalar o actualizar servicios en entornos de Ensayo y Producción. Indique los cambios de servicio necesarios e incluya los `.magento.app.yaml` y `services.yaml` archivos actualizados y la versión de PHP en el ticket. El equipo de infraestructura en la nube puede tardar hasta 48 horas en actualizar el proyecto. Consulte [Software y servicios compatibles](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html?lang=es#supported-software-and-services).

## Compruebe que haya instalado un motor de búsqueda compatible

Adobe Commerce requiere que Elasticsearch u OpenSearch estén instalados para utilizar el software.

**Si está actualizando de 2.3.x a 2.4**, debe comprobar si está utilizando MySQL, Elasticsearch o una extensión de terceros como motor de búsqueda del catálogo en su instancia de 2.3.x. El resultado determina lo que debe hacer _antes de_ actualizar a 2.4.

**Si está actualizando revisiones en las líneas de versión 2.3.x o 2.4.x**, si Elasticsearch 7.x ya está instalado, puede [migrar de forma opcional a OpenSearch](opensearch-migration.md).

Puede utilizar la línea de comandos o el administrador para determinar el motor de búsqueda del catálogo:

* Escriba el comando `bin/magento config:show catalog/search/engine`. El comando devuelve un valor de `mysql`, `elasticsearch` (que indica que Elasticsearch 2 está configurado), `elasticsearch5`, `elasticsearch6`, `elasticsearch7` o un valor personalizado, lo que indica que ha instalado un motor de búsqueda de terceros. Para las versiones anteriores a 2.4.6, utilice el valor `elasticsearch7` para el motor Elasticsearch 7 u OpenSearch. Para la versión 2.4.6 y posterior, utilice el valor `opensearch` para el motor OpenSearch.

* En Admin, compruebe el valor del campo **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]**.

Las secciones siguientes describen qué acciones debe realizar antes de actualizar a 2.4.0.

### MySQL

A partir de la versión 2.4, MySQL ya no es un motor de búsqueda de catálogo compatible. Debe instalar y configurar Elasticsearch o OpenSearch antes de actualizar. Utilice los siguientes recursos para guiarle a través de este proceso:

* [Instalación y configuración de Elasticsearch](../../configuration/search/overview-search.md)
* [Instalando Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* Configure [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) o [Apache](../../installation/prerequisites/search-engine/configure-apache.md) para que funcionen con el motor de búsqueda
* [Configurar Commerce para usar Elasticsearch](../../configuration/search/configure-search-engine.md) y reindexar

Algunos motores de búsqueda de catálogos de terceros se ejecutan sobre el motor de búsqueda de Adobe Commerce. Póngase en contacto con el proveedor para determinar si debe actualizar la extensión.

### Cambios de MySQL 8.4

Adobe agregó compatibilidad con MySQL 8.4 en la versión 2.4.8.
Esta sección describe los cambios más importantes en MySQL 8.4 que los desarrolladores deben tener en cuenta.

#### Clave no estándar obsoleta

El uso de claves no únicas o parciales como claves externas no es estándar y está obsoleto en MySQL 8.4. A partir de MySQL 8.4.0, debe habilitar explícitamente dichas claves estableciendo [`restrict_fk_on_non_standard_key`](https://dev.mysql.com/doc/refman/8.4/en/server-system-variables.html#sysvar_restrict_fk_on_non_standard_key) en `OFF` o iniciando el servidor con la opción `--skip-restrict-fk-on-non-standard-key`.

#### Actualización de MySQL 8.0 ( o versiones anteriores ) a MySQL 8.4

Para actualizar correctamente MySQL de la versión 8.0 a la versión 8.4, debe seguir estos pasos en orden:

1. Activar modo de mantenimiento:

   ```bash
   bin/magento maintenance:enable
   ```

1. Hacer una copia de seguridad de base de datos:

   ```bash
   bin/magento setup:backup --db
   ```

1. Actualice MySQL a la versión 8.4.
1. Establecer `restrict_fk_on_non_standard_key` en `OFF` en `[mysqld]` en el archivo `my.cnf`.

   ```bash
   [mysqld]
   restrict_fk_on_non_standard_key = OFF 
   ```

   >[!WARNING]
   >
   >Si no cambia el valor de `restrict_fk_on_non_standard_key` a `OFF`, obtendrá el siguiente error durante la importación:
   >
   >```sql
   > ERROR 6125 (HY000) at line 2164: Failed to add the foreign key constraint. Missing unique key for constraint 'CAT_PRD_FRONTEND_ACTION_PRD_ID_CAT_PRD_ENTT_ENTT_ID' in the referenced table 'catalog_product_entity'
   >```
1. Reinicie el servidor MySQL.
1. Importe los datos de copia de seguridad en MySQL.
1. Limpie la caché:

   ```bash
   bin/magento cache:clean
   ```

1. Desactivar el modo de mantenimiento:

   ```bash
   bin/magento maintenance:disable
   ```

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### Motor de búsqueda

Debe instalar y configurar Elasticsearch 7.6 o superior o OpenSearch 1.2 antes de actualizar a 2.4.0. Adobe ya no es compatible con Elasticsearch 2.x, 5.x y 6.x. [Configuración del motor de búsqueda](../../configuration/search/configure-search-engine.md) en la _Guía de configuración_ describe las tareas que debe realizar después de actualizar Elasticsearch a una versión compatible.

Consulte [Actualización de Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) para obtener instrucciones completas sobre cómo realizar copias de seguridad de los datos, detectar posibles problemas de migración y probar actualizaciones antes de implementarlas en producción. Según la versión actual de Elasticsearch, puede que sea necesario o no reiniciar el clúster por completo.

Elasticsearch requiere Java Development Kit (JDK) 1.8 o superior. Consulte [Instalar el Kit de desarrollo de software de Java (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) para comprobar qué versión de JDK está instalada.

#### OpenSearch

OpenSearch es una ramificación de código abierto de Elasticsearch 7.10.2, tras el cambio de licencia de Elasticsearch. Las siguientes versiones de Adobe Commerce son compatibles con OpenSearch:

* 2.4.6 (OpenSearch tiene un módulo y una configuración independientes)
* 2.4.5
* 2.4.4
* 2.4.3-p2
* 2.3.7-p3

Solo puede [migrar de Elasticsearch a OpenSearch](opensearch-migration.md) si está actualizando a una versión de Adobe Commerce de la lista anterior (o superior).

OpenSearch requiere JDK 1.8 o superior. Consulte [Instalar el Kit de desarrollo de software de Java (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) para comprobar qué versión de JDK está instalada.

[Configuración del motor de búsqueda](../../configuration/search/configure-search-engine.md) describe las tareas que debe realizar después de cambiar los motores de búsqueda.

#### Actualizar Elasticsearch

La compatibilidad con Elasticsearch 8.x se introdujo en Adobe Commerce 2.4.6. Las siguientes instrucciones muestran un ejemplo de actualización de Elasticsearch de 7.x a 8.x:

>[!NOTE]
>
>En la próxima versión de 2.4.8, estos pasos no serán necesarios porque el módulo de Elasticsearch 8 está incluido de forma predeterminada y no es necesario instalarlo por separado.

1. Actualice el servidor de Elasticsearch 7.x a 8.x y asegúrese de que está en funcionamiento. Consulte la [documentación de Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Habilite el campo `id_field_data` agregando la siguiente configuración al archivo `elasticsearch.yml` y reiniciando el servicio Elasticsearch 8.x.

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >Para admitir Elasticsearch 8.x, Adobe Commerce 2.4.6 deshabilita la propiedad `indices.id_field_data` de forma predeterminada y utiliza el campo `_id` en la propiedad `docvalue_fields`.

1. En el directorio raíz del proyecto de Adobe Commerce, actualice las dependencias del Compositor para quitar el módulo `Magento_Elasticsearch7` e instalar el módulo `Magento_Elasticsearch8`.

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

   Si encuentra un error de dependencia para `psr/http-message`, haga clic para expandir la siguiente sección de solución de problemas:

   +++Resolución de problemas

   Si encuentra conflictos de dependencia al instalar Elasticsearch 8, especialmente con `psr/http-message`, puede resolverlos siguiendo estos pasos:

   1. En primer lugar, requiera el módulo de Elasticsearch 8 sin actualizar otras dependencias:

      ```bash
      composer require magento/module-elasticsearch-8 --no-update
      ```

   1. A continuación, actualice el módulo Elasticsearch 8 y los paquetes `aws/aws-sdk-php`:

      ```bash
      composer update magento/module-elasticsearch-8 aws/aws-sdk-php -W
      ```

   Este enfoque funciona para 2.4.7-p4 con PHP 8.3. El problema se debe a que `aws/aws-sdk-php` requiere `psr/http-message >= 2.0`, lo que puede causar conflictos. Los pasos anteriores ayudan a resolver estos problemas de dependencia.

   +++

1. Actualice los componentes del proyecto.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configurar Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) en [!DNL Admin].

1. Reindexe el índice del catálogo.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Elimine todos los elementos de los tipos de caché habilitados.

   ```bash
   bin/magento cache:clean
   ```

#### Degradar Elasticsearch

Si actualiza de forma involuntaria la versión de Elasticsearch en el servidor o determina que necesita degradarla por cualquier otro motivo, también debe actualizar las dependencias del proyecto de Adobe Commerce. Por ejemplo, para reducir de Elasticsearch 8.x a 7.x

1. Actualice el servidor de Elasticsearch 8.x a 7.x y asegúrese de que está en funcionamiento. Consulte la [documentación de Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. En el directorio raíz del proyecto de Adobe Commerce, actualice las dependencias de Composer para quitar el módulo `Magento_Elasticsearch8` y sus dependencias de Composer e instale el módulo `Magento_Elasticsearch7`.

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. Actualice los componentes del proyecto.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configurar Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) en [!DNL Admin].

1. Reindexe el índice del catálogo.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Elimine todos los elementos de los tipos de caché habilitados.

   ```bash
   bin/magento cache:clean
   ```

### Extensiones de terceros

Le recomendamos que se ponga en contacto con el proveedor del motor de búsqueda para determinar si la extensión es totalmente compatible con una versión de Adobe Commerce.

## Convertir formato de tabla de base de datos

Debe convertir el formato de todas las tablas de base de datos de `COMPACT` a `DYNAMIC`. También debe convertir el tipo de motor de almacenamiento de `MyISAM` a `InnoDB`. Ver [prácticas recomendadas](../../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md).

## Establecer el límite de archivos abiertos

Establecer el límite (ulimit) de archivos abiertos puede ayudar a evitar errores en varias llamadas recursivas de cadenas de consulta largas o problemas con el uso del comando `bin/magento setup:rollback`. Este comando es diferente para diferentes shells de UNIX. Consulte su sabor individual para obtener detalles específicos sobre el comando `ulimit`.

Adobe recomienda establecer los archivos abiertos [ulimit](https://ss64.com/bash/ulimit.html) en un valor de `65536` o más, pero puede usar un valor mayor si es necesario. Puede establecer el ulimit en la línea de comandos o convertirlo en un ajuste permanente para el shell del usuario.

Para establecer el ulimit desde la línea de comandos:

1. Cambiar al [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Establezca el ulimit en `65536`.

   ```bash
   ulimit -n 65536
   ```

Para establecer el valor en su shell de Bash:

1. Cambiar al [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Abra `/home/<username>/.bashrc` en un editor de texto.
1. Añada la línea siguiente:

   ```bash
   ulimit -n 65536
   ```

1. Guarde los cambios en el archivo `.bashrc` y salga del editor de texto.

>[!IMPORTANT]
>
>Le recomendamos que evite establecer un valor para la propiedad `pcre.recursion_limit` en el archivo `php.ini`, ya que puede provocar reversiones incompletas sin previo aviso de error.

## Verificar que los trabajos cron se estén ejecutando

El programador de tareas de UNIX `cron` es fundamental para las operaciones diarias de Adobe Commerce. Programa cosas como la reindexación, los boletines informativos, los correos electrónicos y los mapas del sitio. Varias funciones requieren que al menos un trabajo cron se ejecute como propietario del sistema de archivos.

Para comprobar que el trabajo de cron está configurado correctamente, compruebe el crontab introduciendo el siguiente comando como propietario del sistema de archivos:

>[!NOTE]
>
>El crontab es el archivo de configuración responsable de ejecutar los trabajos cron.

```bash
crontab -l
```

Se deben mostrar resultados similares a los siguientes:

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

Otro síntoma de que cron no se está ejecutando es el siguiente error en el administrador:

![Mensajes del sistema - cron no se está ejecutando](../../assets/upgrade-guide/cron-not-running.png)

Para ver el error, haga clic en **Mensajes del sistema** en la parte superior de la ventana de la siguiente manera:

![Notificación de mensajes del sistema](../../assets/upgrade-guide/system-messages.png)

Consulte [Configurar y ejecutar cron](../../configuration/cli/configure-cron-jobs.md) para obtener más información.

## Definir DATA_CONVERTER_BATCH_SIZE

Adobe Commerce 2.4 incluye mejoras de seguridad que requieren que algunos datos se conviertan de serializados a JSON. Esta conversión se produce durante la actualización y puede tardar mucho tiempo, según la cantidad de datos que haya en la base de datos.

Las siguientes tablas son las más afectadas:

* `catalogrule`
* `core_config_data`
* `magento_reward_history`
* `quote_payment`
* `quote`
* `sales_order_payment`
* `sales_order`
* `salesrule`
* `url_rewrite`

Si tiene una gran cantidad de datos, puede mejorar el rendimiento estableciendo el valor de una variable de entorno, `DATA_CONVERTER_BATCH_SIZE`. De manera predeterminada, el valor se establece en `50,000`.

Para establecer la variable de entorno:

1. Cambiar al [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Configure la variable:

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` requiere memoria; evite configurarla en un valor grande (aproximadamente 1 GB) sin probarla primero.

1. Una vez completada la actualización, puede anular el ajuste de la variable:

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Comprobar permisos del sistema de archivos

Por motivos de seguridad, Adobe Commerce requiere ciertos permisos en el sistema de archivos. Los permisos son diferentes de _[propiedad](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. La propiedad determina quién puede realizar acciones en el sistema de archivos; los permisos determinan lo que el usuario puede hacer.

El grupo [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md) debe poder escribir en los directorios del sistema de archivos.

Para comprobar que los permisos del sistema de archivos están correctamente configurados, inicie sesión en el servidor de aplicaciones o utilice la aplicación de administrador de archivos del proveedor de alojamiento.

Por ejemplo, escriba el siguiente comando si la aplicación está instalada en `/var/www/html/magento2`:

```bash
ls -l /var/www/html/magento2
```

Salida de ejemplo:

```console
total 1028
drwxrwx---. 12 magento_user apache   4096 Jun  7 07:55 .
drwxr-xr-x.  3 root         root     4096 May 11 14:29 ..
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 app
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 bin
-rw-rw----.  1 magento_user apache 439792 Apr 27 21:23 CHANGELOG.md
-rw-rw----.  1 magento_user apache   3422 Apr 27 21:23 composer.json
-rw-rw----.  1 magento_user apache 425214 Apr 27 21:27 composer.lock
-rw-rw----.  1 magento_user apache   3425 Apr 27 21:23 CONTRIBUTING.md
-rw-rw----.  1 magento_user apache  10011 Apr 27 21:23 CONTRIBUTOR_LICENSE_AGREEMENT.html
-rw-rw----.  1 magento_user apache    631 Apr 27 21:23 COPYING.txt
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 dev
-rw-rw----.  1 magento_user apache   2926 Apr 27 21:23 Gruntfile.js
-rw-rw----.  1 magento_user apache   7592 Apr 27 21:23 .htaccess
-rw-rw----.  1 magento_user apache   6419 Apr 27 21:23 .htaccess.sample
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 lib
-rw-rw----.  1 magento_user apache  10376 Apr 27 21:23 LICENSE_AFL.txt
-rw-rw----.  1 magento_user apache  30634 Apr 27 21:23 LICENSE_EE.txt
-rw-rw----.  1 magento_user apache  10364 Apr 27 21:23 LICENSE.txt
-rw-rw----.  1 magento_user apache   4108 Apr 27 21:23 nginx.conf.sample
-rw-rw----.  1 magento_user apache   1427 Apr 27 21:23 package.json
-rw-rw----.  1 magento_user apache   1659 Apr 27 21:23 .php_cs
-rw-rw----.  1 magento_user apache    804 Apr 27 21:23 php.ini.sample
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 phpserver
drwxrwx---.  6 magento_user apache   4096 Jun  7 07:53 pub
-rw-rw----.  1 magento_user apache   2207 Apr 27 21:23 README_EE.md
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 setup
-rw-rw----.  1 magento_user apache   3731 Apr 27 21:23 .travis.yml
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 update
drwxrws---. 11 magento_user apache   4096 Jun 13 16:05 var
drwxrws---. 29 magento_user apache   4096 Jun  7 07:53 vendor
```

Consulte lo siguiente para obtener una explicación del resultado del ejemplo:

* La mayoría de los archivos son `-rw-rw----`, que es `660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* El propietario del sistema de archivos es `magento_user`

Para obtener información más detallada, puede introducir el siguiente comando:

```bash
ls -la /var/www/html/magento2/pub
```

Dado que Adobe Commerce implementa recursos de archivos estáticos en subdirectorios de `pub`, es aconsejable comprobar allí también los permisos y la propiedad.

Para obtener más información, consulte [Permisos y propiedad del sistema de archivos](../../installation/prerequisites/file-system/overview.md).

## Establecer la raíz del directorio `pub/`

Consulte [Modificar docroot para mejorar la seguridad](../../installation/tutorials/docroot.md) para obtener más información.

## Instalación del complemento de actualización del Compositor

El complemento [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) Composer resuelve los cambios que deben realizarse en el archivo del proyecto raíz `composer.json` antes de actualizar a un nuevo requisito de producto.

El complemento automatiza parcialmente la actualización manual al identificar y ayudarle a resolver conflictos de dependencia en lugar de requerir que los identifique y corrija manualmente.

Para instalar el complemento:

1. Agregue el paquete a su archivo `composer.json`.

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. Actualice las dependencias:

   ```bash
   composer update
   ```
