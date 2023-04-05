---
title: Configuración de la aplicación
description: Obtenga información sobre la configuración posterior a la instalación necesaria para las implementaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---


# Configuración de la aplicación

Cuando haya terminado de instalar Adobe Commerce o Magento Open Source, debe configurarlo. En este tema se proporcionan algunos ajustes de configuración recomendados.

## Configuración de cron

El programador de tareas UNIX, cron, es fundamental para las operaciones diarias de la aplicación. Programa cosas como la reindexación, boletines informativos, correos electrónicos y mapas del sitio. A *crontab* es una configuración de cron.

Debe instalar Adobe Commerce y los servicios de Magento Open Source en la *crontab*, o algunas funciones principales (y algunas extensiones de terceros) no funcionan correctamente.

Para obtener más información sobre cron, como cómo quitar un crontab y ejecutar cron desde la línea de comandos, consulte [Configuración y ejecución de cron](../../configuration/cli/configure-cron-jobs.md).

## Configuración y recomendaciones de seguridad

Después de la instalación, se recomienda lo siguiente:

* Asegúrese de que la propiedad y los permisos del archivo estén correctamente configurados
* Recomendamos encarecidamente [cambio del URI de administrador predeterminado](../tutorials/admin-uri.md) from `admin` a otra cosa
* Asegúrese de que la variable [`X-Frame-Option` Encabezado HTTP](../../configuration/security/xframe-options.md) está configurado correctamente.
* Tome precauciones contra la ejecución de scripts en sitios múltiples (XSS) por [seguridad de las plantillas](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

Si ha instalado [clonación del repositorio de GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/), asegúrese de que, cuando implemente la aplicación, solo incluya los archivos y carpetas necesarios para el entorno de producción. Los archivos y carpetas que no son necesarios pueden exponer riesgos de seguridad.

## Habilitar las reescrituras del servidor Apache

Si utiliza el servidor web Apache, debe habilitar las reescrituras del servidor para que las páginas se muestren correctamente. De lo contrario, verá páginas sin estilos y otros problemas.

[Sección en reescrituras del servidor Apache](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## Almacenamiento en caché en un entorno de varios nodos web

Si tiene varios nodos web, *cannot* utilice el almacenamiento en caché predeterminado de archivos de la aplicación porque no hay sincronización entre nodos web. En otras palabras, la actividad de un nodo web solo se escribe en el sistema de archivos de ese nodo web. La actividad siguiente, si se realiza en otro nodo web, puede dar como resultado que se escriban archivos innecesarios o que se produzcan errores.

En su lugar, utilice [Redis](../../configuration/cache/config-redis.md) para la caché predeterminada y la caché de página.

## Configuración del servidor

Esta sección describe brevemente la configuración que le recomendamos tener en cuenta para el servidor en el que se ejecuta la aplicación. Algunos de estos ajustes no están directamente relacionados con la aplicación; se proporcionan únicamente como sugerencias.

### Rotación de registro

UNIX `logrotate` permite administrar sistemas que generan una gran cantidad de archivos de registro. Permite la rotación, compresión, eliminación y envío automáticos de archivos de registro. Cada archivo de registro se puede administrar diariamente, semanalmente, mensualmente o cuando el archivo de registro supere el tamaño especificado.

Para obtener más información, consulte uno de los siguientes temas:

* [Cómo: Tutorial de comando de rotación de registro definitivo con diez ejemplos](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [Apilar Exchange](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` página principal](https://linuxconfig.org/logrotate-8-manual-page)

### Configure las reglas iptables para permitir que varios servicios se comuniquen

Tanto si tiene un servidor como si tiene muchos, debe abrir los puertos en el cortafuegos para permitir que los servicios se comuniquen. Por ejemplo, si utiliza el motor de búsqueda Solr con Adobe Commerce, debe habilitarlo para comunicarse con el servidor web. Si tiene varios nodos web, debe permitirles comunicarse entre sí.

Más información:

* Ubuntu: [Página de documentación de Ubuntu](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [Instrucciones de CentOS](https://wiki.centos.org/HowTos/Network/IPTables).

### Reglas mejoradas de seguridad de Linux (SELinux)

No tenemos una recomendación para si usa SELinux; sin embargo, si lo utiliza, debe configurar los servicios para que se comuniquen entre sí de forma similar a la configuración de iptables.

Más información:

* Ubuntu: [Manual de Debian](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [Wiki de CentOS](https://wiki.centos.org/HowTos/SELinux)

### Configuración de un servidor de correo electrónico

Adobe Commerce y Magento Open Source requieren un servidor de correo electrónico. No recomendamos un servidor en particular, pero puede probar cualquiera de los siguientes métodos:

* Postfix para CentOS ([Tutorial sobre océano digital](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [Documentación de CentOS](https://www.centos.org))
* Postfix para Ubuntu ([Tutorial sobre océano digital](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Documentación de Ubuntu](https://help.ubuntu.com/community/MailServer))

### Refine el motor de búsqueda para obtener un rendimiento mejorado:

Elasticsearch o OpenSearch es necesario para todas las instalaciones a partir de 2.4.0.

* [Instalación y configuración del motor de búsqueda](../../configuration/search/overview-search.md)

### Configuración de una cola de mensajes

Desde la versión 2.3.0, Adobe Commerce y Magento Open Source incluyen funcionalidad de cola de mensajes. En versiones anteriores, solo está disponible para Adobe Commerce.

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Configuración solo para Adobe Commerce

Solo puede configurar lo siguiente si utiliza Adobe Commerce:

* [Dividir bases de datos para cierre de compra, administración de pedidos y otras tablas de base de datos](../../configuration/storage/multi-master.md)
