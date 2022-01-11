---
title: Requisitos previos completos
description: Prepare su proyecto de Adobe Commerce o Magento Open Source para una actualización completando estos pasos previos.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '1316'
ht-degree: 0%

---


# Requisitos previos de actualización completos

Es importante comprender qué es necesario para ejecutar Adobe Commerce o Magento Open Source. Primero debe revisar el [requisitos del sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) para la versión a la que planea actualizar.

Después de revisar los requisitos del sistema, debe completar los siguientes requisitos previos antes de actualizar el sistema:

- Actualizar todo el software
- Compruebe que el Elasticsearch esté instalado
- Establecer el límite de archivos abiertos
- Compruebe que se estén ejecutando trabajos cron
- Establezca `DATA_CONVERTER_BATCH_SIZE`
- Comprobar permisos del sistema de archivos
- Configure las variables `pub/` raíz de directorio
- Instalación del complemento de actualización del Compositor

## Actualizar todo el software

La variable [requisitos del sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) describa exactamente qué versiones de software de terceros se han probado con las versiones de Adobe Commerce y Magento Open Source.

Asegúrese de haber actualizado todos los requisitos y dependencias del sistema en su entorno. Consulte PHP [7,4](https://www.php.net/manual/en/migration74.php), PHP [8,0](https://www.php.net/manual/en/migration80.php), PHP [8,1](https://www.php.net/manual/en/migration81.php)y [configuración requerida de PHP](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html#php-required-set).

## Verificar que el Elasticsearch esté instalado

Adobe Commerce y Magento Open Source requieren que se instale Elasticsearch para utilizar el software. Antes de actualizar de 2.3.x a 2.4, debe comprobar si utiliza MySQL, Elasticsearch o una extensión de terceros como motor de búsqueda de catálogo en la instancia 2.3.x. El resultado determina lo que debe hacer _before_ actualización a 2.4.

Puede utilizar la línea de comandos o el administrador para determinar el motor de búsqueda del catálogo:

- Introduzca la variable `bin/magento config:show catalog/search/engine` comando. El comando devuelve un valor de `mysql`, `elasticsearch` (lo que indica que el Elasticsearch 2 está configurado), `elasticsearch5`, `elasticsearch6`, `elasticsearch7`, o un valor personalizado, que indica que ha instalado un motor de búsqueda de terceros.

- En el Administrador, compruebe el valor de la variable **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** campo .

Las secciones siguientes describen las acciones que debe realizar antes de actualizar a la versión 2.4.0.

### MySQL

A partir de la versión 2.4, MySQL ya no es un motor de búsqueda de catálogo compatible. Debe instalar y configurar el Elasticsearch antes de actualizar. Utilice los siguientes recursos para ayudarle a guiar a través de este proceso:

- [Instalación y configuración del Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-overview.html)
- [Instalación del Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- Configuración del Elasticsearch para trabajar con [nginx](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-config-nginx.html) o [Apache](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-config-apache.html)
- [Configuración de Commerce para utilizar Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) y reindexar

Algunos motores de búsqueda de catálogo de terceros se ejecutan sobre el motor de búsqueda de Adobe Commerce. Póngase en contacto con el proveedor para determinar si debe actualizar la extensión.

### Elasticsearch

Debe instalar y configurar Elasticsearch antes de actualizar a 2.4.0. Adobe ya no es compatible con Elasticsearch 2.x, 5.x y 6.x.

Consulte [Actualización del Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) para obtener instrucciones completas sobre cómo realizar copias de seguridad de los datos, detectar posibles problemas de migración y probar actualizaciones antes de implementarlas en producción. Según la versión actual del Elasticsearch, puede que sea necesario o no reiniciar el clúster completo.

Elasticsearch requiere JDK 1.8 o superior. Consulte [Instalación del Kit de desarrollo de software de Java (JDK)](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) para comprobar qué versión de JDK está instalada.

[Configuración del Magento para utilizar el Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) describe las tareas que debe realizar después de actualizar el Elasticsearch 2 a una versión compatible.

### Extensiones de terceros

Le recomendamos que se ponga en contacto con el proveedor de motores de búsqueda para determinar si la extensión es totalmente compatible con la versión 2.4.

## Establecer el límite de archivos abiertos

La configuración del límite de archivos abiertos (ulimit) puede ayudar a evitar fallos en varias llamadas recursivas de cadenas de consulta largas o problemas con el uso de la variable `bin/magento setup:rollback` comando. Este comando es diferente para diferentes conchas UNIX. Consulte su sabor individual para obtener detalles específicos sobre la variable `ulimit` comando.

Adobe recomienda configurar los archivos abiertos [ulimit](http://ss64.com/bash/ulimit.html) a un valor de `65536` o más, pero puede utilizar un valor mayor si es necesario. Puede establecer el límite en la línea de comandos o puede convertirlo en una configuración permanente para el shell del usuario.

Para establecer el límite desde la línea de comandos:

1. Cambie a la [propietario del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Establezca el límite en 65536.

   ```bash
   ulimit -s 65536
   ```

   >[!NOTE]
   >
   > La sintaxis para el límite de archivos abiertos depende del shell de UNIX que utilice. La configuración anterior debería funcionar con CentOS y Ubuntu con el shell de Bash. Sin embargo, para el sistema operativo Mac, la configuración correcta es ulimit -S 65532. Consulte una página de comando man o referencia del sistema operativo para obtener más información.

Para establecer el valor en el shell de Bash:

1. Cambie a la [propietario del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Apertura `/home/<username>/.bashrc` en un editor de texto.
1. Añada la siguiente línea:

   ```bash
   ulimit -s 65536
   ```

1. Guarde los cambios en la `.bashrc` y salga del editor de texto.

>[!IMPORTANT]
>
>Le recomendamos que evite establecer un valor para la variable `pcre.recursion_limit` en la variable `php.ini` porque puede provocar devoluciones incompletas sin aviso de error.

## Verificar que los trabajos de cron se estén ejecutando

El programador de tareas de UNIX `cron` es fundamental para las operaciones diarias de Adobe Commerce y Magento Open Source. Programa cosas como la reindexación, boletines informativos, correos electrónicos, mapas del sitio, etc. Varias funciones requieren al menos un trabajo cron que se ejecute como propietario del sistema de archivos.

Para verificar que su trabajo cron está configurado correctamente, compruebe crontab introduciendo el siguiente comando como propietario del sistema de archivos:

>[!NOTE]
>
>crontab es el archivo de configuración responsable de ejecutar trabajos cron.

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

Para ver el error, haga clic en **Mensajes del sistema** en la parte superior de la ventana de la siguiente manera:

![](../../assets/upgrade-guide/system-messages.png)

Consulte [Configuración y ejecución de cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) para obtener más información.

## Establezca DATA_CONVERTER_BATCH_SIZE

Adobe Commerce 2.4 incluye mejoras de seguridad que requieren que algunos datos se conviertan de serializados a JSON. Esta conversión se produce durante la actualización y puede tardar mucho tiempo, dependiendo de la cantidad de datos que haya en la base de datos.

Las siguientes tablas se ven más afectadas:

- `catalogrule`
- `core_config_data`
- `magento_reward_history`
- `quote_payment`
- `quote`
- `sales_order_payment`
- `sales_order`
- `salesrule`
- `url_rewrite`

Si tiene una gran cantidad de datos, puede mejorar el rendimiento configurando el valor de una variable de entorno. `DATA_CONVERTER_BATCH_SIZE`. De forma predeterminada, el valor se establece en `50,000`.

Para configurar la variable de entorno:

1. Cambie a la [propietario del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Configure la variable :

   ```bash
   export DATA_CONVERTER_BATCH_SIZE 100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` requiere memoria; evite configurarlo en un valor grande (aproximadamente 1 GB) sin probarlo primero.

1. Una vez completada la actualización, puede desactivar la variable :

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Comprobar permisos del sistema de archivos

Por motivos de seguridad, Adobe Commerce y el Magento Open Source requieren ciertos permisos en el sistema de archivos. Los permisos son diferentes de _[propiedad](https://devdocs.magento.com/guides/v2.4/comp-mgr/prereq/prereq_compman-checklist.html#magento-owner-group)_. La propiedad determina quién puede realizar acciones en el sistema de archivos; los permisos determinan lo que puede hacer el usuario.

Los directorios del sistema de archivos deben ser grabables por el [del propietario del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html) grupo.

Para comprobar que los permisos del sistema de archivos están correctamente configurados, inicie sesión en el servidor de aplicaciones o utilice la aplicación del administrador de archivos de su proveedor de alojamiento.

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

Consulte lo siguiente para obtener una explicación de la salida de muestra:

- La mayoría de los archivos son `-rw-rw----`, que es `660`
- `drwxrwx---` = `770`
- `-rw-rw-rw-` = `666`
- El propietario del sistema de archivos es `magento_user`

Para obtener información más detallada, puede introducir el siguiente comando:

```bash
ls -la /var/www/html/magento2/pub
```

Porque Adobe Commerce y el Magento Open Source implementan recursos de archivos estáticos en subdirectorios de `pub`, es aconsejable verificar los permisos y la propiedad allí también.

Para obtener más información, consulte [Permisos y propiedad del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

## Configure las variables `pub/` raíz de directorio

Consulte [Modificar docroot para mejorar la seguridad](https://devdocs.magento.com/guides/v2.4/install-gde/tutorials/change-docroot-to-pub.html) para obtener más información.

## Instalación del complemento de actualización del Compositor

La variable [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) El complemento Composer resuelve los cambios que se deben realizar en el proyecto raíz `composer.json` antes de actualizar a un nuevo requisito de producto.

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
