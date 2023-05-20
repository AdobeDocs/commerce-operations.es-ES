---
title: Completar requisitos previos
description: Prepare su proyecto de Adobe Commerce para una actualización completando estos pasos previos.
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---

# Completar requisitos previos de actualización

Es importante comprender lo necesario para ejecutar Adobe Commerce. Primero debe revisar la [requisitos del sistema](../../installation/system-requirements.md) para la versión a la que planea actualizar.

Después de revisar los requisitos del sistema, debe completar los siguientes requisitos previos antes de actualizar el sistema:

* Actualizar todo el software
* Compruebe que haya instalado un motor de búsqueda compatible
* Convertir formato de tabla de base de datos
* Establecer el límite de archivos abiertos
* Verificar que los trabajos cron se estén ejecutando
* Establecer `DATA_CONVERTER_BATCH_SIZE`
* Comprobar permisos del sistema de archivos
* Configure las variables `pub/` raíz de directorio
* Instalación del complemento de actualización del Compositor

## Actualizar todo el software

El [requisitos del sistema](../../installation/system-requirements.md) describa exactamente qué versiones de software de terceros se han probado con las versiones de Adobe Commerce.

Asegúrese de haber actualizado todos los requisitos y dependencias del sistema de su entorno. Consulte PHP [7,4](https://www.php.net/manual/en/migration74.php), PHP [8,0](https://www.php.net/manual/en/migration80.php), PHP [8,1](https://www.php.net/manual/en/migration81.php), y [configuración de PHP requerida](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>Para los proyectos Pro de Adobe Commerce en la infraestructura en la nube, debe crear un [Asistencia](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) para instalar o actualizar servicios en entornos de ensayo y producción. Indique los cambios de servicio necesarios e incluya su `.magento.app.yaml` y `services.yaml` archivos y versión de PHP en el ticket. El equipo de infraestructura en la nube puede tardar hasta 48 horas en actualizar el proyecto. Consulte [Software y servicios compatibles](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services).

## Compruebe que haya instalado un motor de búsqueda compatible

Adobe Commerce requiere que Elasticsearch u OpenSearch estén instalados para utilizar el software.

**Si actualiza de 2.3.x a 2.4**, debe comprobar si está utilizando MySQL, Elasticsearch o una extensión de terceros como motor de búsqueda del catálogo en la instancia 2.3.x. El resultado determina lo que debe hacer _antes_ actualización a 2.4.

**Si actualiza versiones de parches dentro de las líneas de versión 2.3.x o 2.4.x**, si Elasticsearch 7.x ya está instalado, puede [migrar a OpenSearch](opensearch-migration.md).

Puede utilizar la línea de comandos o el administrador para determinar el motor de búsqueda del catálogo:

* Introduzca el `bin/magento config:show catalog/search/engine` comando. El comando devuelve un valor de `mysql`, `elasticsearch` (lo que indica que el Elasticsearch 2 está configurado), `elasticsearch5`, `elasticsearch6`, `elasticsearch7`o un valor personalizado, que indica que ha instalado un motor de búsqueda de terceros. Para versiones anteriores a la 2.4.6, utilice la variable `elasticsearch7` para el Elasticsearch 7 o el motor OpenSearch. Para la versión 2.4.6 y posterior de, utilice el `opensearch` para el motor OpenSearch.

* En Admin, compruebe el valor de **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** field.

Las secciones siguientes describen qué acciones debe realizar antes de actualizar a 2.4.0.

### MySQL

A partir de la versión 2.4, MySQL ya no es un motor de búsqueda de catálogo compatible. Debe instalar y configurar Elasticsearch u OpenSearch antes de actualizar. Utilice los siguientes recursos para guiarle a través de este proceso:

* [Elasticsearch de instalación y configuración](../../configuration/search/overview-search.md)
* [Elasticsearch de instalación](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* Configurar [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) o [Apache](../../installation/prerequisites/search-engine/configure-apache.md) para trabajar con el motor de búsqueda
* [Configuración de Commerce para utilizar Elasticsearch](../../configuration/search/configure-search-engine.md) y reindexar

Algunos motores de búsqueda de catálogos de terceros se ejecutan sobre el motor de búsqueda de Adobe Commerce. Póngase en contacto con el proveedor para determinar si debe actualizar la extensión.

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### Motor de búsqueda

Debe instalar y configurar Elasticsearch 7.6 o superior o OpenSearch 1.2 antes de actualizar a 2.4.0. Adobe ya no es compatible con Elasticsearch 2.x, 5.x y 6.x. [Configuración del motor de búsqueda](../../configuration/search/configure-search-engine.md) en el _Guía de configuración_ describe las tareas que debe realizar después de actualizar Elasticsearch a una versión compatible.

Consulte [Elasticsearch de actualización](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) para obtener instrucciones completas sobre la realización de copias de seguridad de los datos, la detección de posibles problemas de migración y la prueba de actualizaciones antes de su implementación en producción. Según la versión actual del Elasticsearch, puede que sea necesario o no reiniciar el clúster por completo.

Elasticsearch requiere Java Development Kit (JDK) 1.8 o superior. Consulte [Instale el Kit de desarrollo de software de Java (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) para comprobar qué versión de JDK está instalada.

#### OpenSearch

OpenSearch es una ramificación de código abierto de Elasticsearch 7.10.2, tras el cambio de licencia de Elasticsearch. Las siguientes versiones de Adobe Commerce son compatibles con OpenSearch:

* 2.4.6 (OpenSearch tiene un módulo y una configuración independientes)
* 2.4.5
* 2.4.4
* 2.4.3-p2
* 2.3.7-p3

Puede [migrar del Elasticsearch a OpenSearch](opensearch-migration.md) solo si actualiza a una versión de Adobe Commerce de la lista anterior (o posterior).

OpenSearch requiere JDK 1.8 o superior. Consulte [Instale el Kit de desarrollo de software de Java (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) para comprobar qué versión de JDK está instalada.

[Configuración del motor de búsqueda](../../configuration/search/configure-search-engine.md) describe las tareas que debe realizar después de cambiar los motores de búsqueda.

#### Elasticsearch de actualización

La compatibilidad con Elasticsearch 8.x se introdujo en Adobe Commerce 2.4.6. Las siguientes instrucciones muestran un ejemplo de actualización de Elasticsearch de 7.x a 8.x:

1. Actualice el servidor de Elasticsearch 7.x a 8.x y asegúrese de que está en funcionamiento. Consulte la [Documentación del Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Habilite la `id_field_data` al añadir la siguiente configuración a su `elasticsearch.yml` y reiniciar el servicio de Elasticsearch 8.x.

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >Para admitir el Elasticsearch 8.x, Adobe Commerce 2.4.6 deshabilita la `indices.id_field_data` de forma predeterminada y utiliza la propiedad `_id` en el campo `docvalue_fields` propiedad.

1. En el directorio raíz del proyecto de Adobe Commerce, actualice las dependencias del Compositor para eliminar el `Magento_Elasticsearch7` e instale el `Magento_Elasticsearch8` módulo.

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

1. Actualice los componentes del proyecto.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configuración del Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) en el [!DNL Admin].

1. Reindexe el índice del catálogo.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Elimine todos los elementos de los tipos de caché habilitados.

   ```bash
   bin/magento cache:clean
   ```

#### Elasticsearch de downgrade

Si actualiza de forma involuntaria la versión de Elasticsearch en el servidor o determina que necesita degradarla por cualquier otro motivo, también debe actualizar las dependencias del proyecto de Adobe Commerce. Por ejemplo, para reducir de Elasticsearch 8.x a 7.x

1. Cambie el servidor de Elasticsearch 8.x a 7.x y asegúrese de que está en funcionamiento. Consulte la [Documentación del Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. En el directorio raíz del proyecto de Adobe Commerce, actualice las dependencias del Compositor para eliminar el `Magento_Elasticsearch8` y sus dependencias de Compositor, e instale el `Magento_Elasticsearch7` módulo.

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. Actualice los componentes del proyecto.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configuración del Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) en el [!DNL Admin].

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

Debe convertir el formato de todas las tablas de base de datos de `COMPACT` hasta `DYNAMIC`. También debe convertir el tipo de motor de almacenamiento de `MyISAM` hasta `InnoDB`. Consulte [prácticas recomendadas](../../implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.md).

## Establecer el límite de archivos abiertos

Establecer el límite (ulimit) de archivos abiertos puede ayudar a evitar errores en varias llamadas recursivas de cadenas de consulta largas o problemas con el uso del `bin/magento setup:rollback` comando. Este comando es diferente para diferentes shells de UNIX. Consulte su sabor individual para obtener detalles específicos sobre el `ulimit` comando.

El Adobe recomienda configurar los archivos abiertos [ulimit](https://ss64.com/bash/ulimit.html) hasta un valor de `65536` o más, pero puede utilizar un valor mayor si es necesario. Puede establecer el ulimit en la línea de comandos o convertirlo en un ajuste permanente para el shell del usuario.

Para establecer el ulimit desde la línea de comandos:

1. Cambie a la [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Establezca ulimit en `65536`.

   ```bash
   ulimit -n 65536
   ```

Para establecer el valor en su shell de Bash:

1. Cambie a la [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Abrir `/home/<username>/.bashrc` en un editor de texto.
1. Añada la línea siguiente:

   ```bash
   ulimit -n 65536
   ```

1. Guarde los cambios en `.bashrc` y salga del editor de texto.

>[!IMPORTANT]
>
>Se recomienda evitar establecer un valor para `pcre.recursion_limit` propiedad en el `php.ini` porque puede provocar reversiones incompletas sin previo aviso de error.

## Verificar que los trabajos cron se estén ejecutando

El planificador de tareas UNIX `cron` es fundamental para las operaciones diarias de Adobe Commerce. Programa cosas como la reindexación, los boletines informativos, los correos electrónicos y los mapas del sitio. Varias funciones requieren que al menos un trabajo cron se ejecute como propietario del sistema de archivos.

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

![](../../assets/upgrade-guide/cron-not-running.png)

Para ver el error, haga clic en **Mensajes del sistema** en la parte superior de la ventana, como se indica a continuación:

![](../../assets/upgrade-guide/system-messages.png)

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

Si tiene una gran cantidad de datos, puede mejorar el rendimiento configurando el valor de una variable de entorno, `DATA_CONVERTER_BATCH_SIZE`. El valor predeterminado es `50,000`.

Para establecer la variable de entorno:

1. Cambie a la [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
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

Los directorios del sistema de archivos deben poder escribirse mediante el [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md) grupo.

Para comprobar que los permisos del sistema de archivos están correctamente configurados, inicie sesión en el servidor de aplicaciones o utilice la aplicación de administrador de archivos del proveedor de alojamiento.

Por ejemplo, introduzca el siguiente comando si la aplicación está instalada en `/var/www/html/magento2`:

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

Dado que Adobe Commerce implementa recursos de archivos estáticos en subdirectorios de `pub`Sin embargo, es una buena idea verificar los permisos y la propiedad allí también.

Para obtener más información, consulte [Permisos y propiedad del sistema de archivos](../../installation/prerequisites/file-system/overview.md).

## Configure las variables `pub/` raíz de directorio

Consulte [Modifique docroot para mejorar la seguridad](../../installation/tutorials/docroot.md) para obtener más información.

## Instalación del complemento de actualización del Compositor

El [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) El complemento Compositor resuelve los cambios que deben realizarse en el proyecto raíz `composer.json` antes de actualizar a un nuevo requisito de producto.

El complemento automatiza parcialmente la actualización manual al identificar y ayudarle a resolver conflictos de dependencia en lugar de requerir que los identifique y corrija manualmente.

Para instalar el complemento:

1. Añada el paquete a su `composer.json` archivo.

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. Actualice las dependencias:

   ```bash
   composer update
   ```
