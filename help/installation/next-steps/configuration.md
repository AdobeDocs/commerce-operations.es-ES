---
title: Configuración de la aplicación
description: Obtenga información acerca de la configuración posterior a la instalación necesaria para las implementaciones locales de Adobe Commerce y Magento Open Source.
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# Configuración de la aplicación

Ahora que ha terminado de instalar Adobe Commerce o Magento Open Source, debe configurarlo. En este tema se proporcionan algunas opciones de configuración recomendadas.

## Configuración de cron

El programador de tareas de UNIX, cron, es fundamental para las operaciones diarias de la aplicación. Programa cosas como la reindexación, los boletines informativos, los correos electrónicos y los mapas del sitio. A *crontab* es una configuración de cron.

Debe instalar Adobe Commerce y los servicios de Magento Open Source en *crontab*, o algunas funciones principales (y algunas extensiones de terceros) no funcionan correctamente.

Para obtener más información acerca de cron, incluido cómo quitar un crontab y ejecutar cron desde la línea de comandos, consulte [Configurar y ejecutar cron](../../configuration/cli/configure-cron-jobs.md).

## Configuración de seguridad y recomendaciones

Después de la instalación, le recomendamos lo siguiente:

* Asegúrese de que la propiedad y los permisos del archivo estén correctamente configurados
* Recomendamos encarecidamente [cambio del URI de administración predeterminado](../tutorials/admin-uri.md) de `admin` a otra cosa
* Asegúrese de que la [`X-Frame-Option` Encabezado HTTP](../../configuration/security/xframe-options.md) se ha configurado correctamente.
* Tome precauciones contra la ejecución de scripts en sitios múltiples (XSS) al [proteger las plantillas](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

Si ha instalado mediante [clonación del repositorio de GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/), asegúrese de que, al implementar la aplicación, solo incluye los archivos y carpetas necesarios para el entorno de producción. Los archivos y carpetas que no son necesarios pueden exponer potencialmente riesgos de seguridad.

## Habilitar reescrituras del servidor Apache

Si utiliza el servidor web Apache, debe habilitar las reescrituras del servidor para que las páginas se muestren correctamente. De lo contrario, verá páginas sin estilos y otros problemas.

[Sección en las reescrituras del servidor Apache](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## Almacenamiento en caché en un entorno de varios nodos web

Si tiene varios nodos web, puede *no puede* utilice el almacenamiento en caché de archivos predeterminado de la aplicación porque no hay sincronización entre nodos web. En otras palabras, la actividad de un nodo web se escribe solo en el sistema de archivos de ese nodo web. La actividad posterior, si se realiza en otro nodo web, puede provocar que se escriban archivos innecesarios o que se produzcan errores.

En su lugar utilice [Redis](../../configuration/cache/config-redis.md) tanto para la caché predeterminada como para la caché de página.

## Configuración del servidor

En esta sección se describe brevemente la configuración que se recomienda tener en cuenta para el servidor en el que se ejecuta la aplicación. Algunos de estos ajustes no están directamente relacionados con la aplicación; se proporcionan solo como sugerencias.

### Rotación de registro

El UNIX `logrotate` permite administrar sistemas que generan un gran número de archivos de registro. Permite la rotación, la compresión, la eliminación y el envío automáticos de los archivos de registro. Cada archivo de registro se puede administrar diariamente, semanalmente, mensualmente o cuando el archivo de registro supera un tamaño especificado.

Para obtener más información, vea una de las siguientes opciones:

* [Cómo: El tutorial de comando de rotación de registros definitivo con diez ejemplos](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [Stack Exchange](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` página de comando man](https://linuxconfig.org/logrotate-8-manual-page)

### Configure las reglas iptables para permitir que varios servicios se comuniquen

Tanto si tiene un servidor como si tiene varios, debe abrir puertos en el cortafuegos para permitir que los servicios se comuniquen. Por ejemplo, si utiliza el motor de búsqueda de Solr con Adobe Commerce, debe habilitarlo para que se comunique con el servidor web. Si tiene varios nodos web, debe habilitarlos para que se comuniquen entre sí.

Más información:

* Ubuntu: [Página de documentación de Ubuntu](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [Procedimientos de CentOS](https://wiki.centos.org/HowTos/Network/IPTables).

### Reglas de seguridad mejorada de Linux (SELinux)

No tenemos una recomendación para si usa SELinux; sin embargo, si lo usa, debe configurar los servicios para comunicarse entre sí de manera similar a configurar iptables.

Más información:

* Ubuntu: [Manual de Debian](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [Wiki de CentOS](https://wiki.centos.org/HowTos/SELinux)

### Configurar un servidor de correo electrónico

Adobe Commerce y Magento Open Source requieren un servidor de correo electrónico. No recomendamos un servidor en particular, pero puede probar cualquiera de los siguientes métodos:

* Postfijo para CentOS ([Tutorial de Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [Documentación de CentOS](https://www.centos.org))
* Postfijo para Ubuntu ([Tutorial de Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Documentación de Ubuntu](https://help.ubuntu.com/community/MailServer))

### Refine el motor de búsqueda para obtener un rendimiento mejorado:

Se requiere Elasticsearch o OpenSearch para todas las instalaciones a partir de la versión 2.4.0.

* [Instalación y configuración del motor de búsqueda](../../configuration/search/overview-search.md)

### Configuración de una cola de mensajes

Desde la versión 2.3.0, Adobe Commerce y Magento Open Source incluyen la funcionalidad de cola de mensajes. En versiones anteriores, solo está disponible para Adobe Commerce.

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Configuración solo para Adobe Commerce

Solo puede configurar lo siguiente si utiliza Adobe Commerce:

* [Dividir bases de datos para cierres de compra, administración de pedidos y otras tablas de base de datos](../../configuration/storage/multi-master.md)
