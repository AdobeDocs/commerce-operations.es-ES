---
title: Configuración de la aplicación
description: Obtenga información acerca de la configuración posterior a la instalación necesaria para las implementaciones locales de Adobe Commerce.
feature: Install, Configuration
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: a7c98879e027948fc887e28d4baa5fb04214ca95
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# Configuración de la aplicación

Ahora que ha terminado de instalar Adobe Commerce, debe configurarlo. En este tema se proporcionan algunas opciones de configuración recomendadas.

## Configuración de cron

El programador de tareas de UNIX, cron, es fundamental para las operaciones diarias de la aplicación. Programa cosas como la reindexación, los boletines informativos, los correos electrónicos y los mapas del sitio. Un *crontab* es una configuración de cron.

Debe instalar los servicios de Adobe Commerce en *crontab*, o alguna funcionalidad principal (y algunas extensiones de terceros) no funcionará correctamente.

Para obtener más información sobre cron, incluido cómo quitar un crontab y ejecutar cron desde la línea de comandos, consulte [Configurar y ejecutar cron](../../configuration/cli/configure-cron-jobs.md).

## Configuración de seguridad y recomendaciones

Después de la instalación, le recomendamos lo siguiente:

* Asegúrese de que la propiedad y los permisos del archivo estén establecidos [correctamente](../prerequisites/file-system/configure-permissions.md)
* Recomendamos [cambiar el URI de administrador predeterminado](../tutorials/admin-uri.md) de `admin` a otra cosa
* Asegúrese de que el encabezado HTTP [`X-Frame-Option` &#x200B;](../../configuration/security/xframe-options.md) esté configurado correctamente.
* Tome precauciones contra los scripts entre sitios (XSS) al [proteger sus plantillas](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

Si ha instalado [clonando el repositorio de GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/), asegúrese de que al implementar la aplicación solo incluya los archivos y carpetas necesarios para el entorno de producción. Los archivos y carpetas que no son necesarios pueden exponer potencialmente riesgos de seguridad.

## Habilitar reescrituras del servidor Apache

Si utiliza el servidor web Apache, debe habilitar las reescrituras del servidor para que las páginas se muestren correctamente. De lo contrario, verá páginas sin estilos y otros problemas.

[Sección en las reescrituras del servidor Apache](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## Almacenamiento en caché en un entorno de varios nodos web

Si tiene varios nodos web, *no puede* usar el almacenamiento en caché de archivos predeterminado de la aplicación porque no hay sincronización entre los nodos web. En otras palabras, la actividad de un nodo web se escribe solo en el sistema de archivos de ese nodo web. La actividad posterior, si se realiza en otro nodo web, puede provocar que se escriban archivos innecesarios o que se produzcan errores.

En su lugar, use [Redis](../../configuration/cache/config-redis.md) tanto para la caché predeterminada como para la caché de la página.

## Configuración del servidor

En esta sección se describe brevemente la configuración que se recomienda tener en cuenta para el servidor en el que se ejecuta la aplicación. Algunos de estos ajustes no están directamente relacionados con la aplicación; se proporcionan solo como sugerencias.

### Rotación de registro

La utilidad UNIX `logrotate` permite administrar sistemas que generan grandes cantidades de archivos de registro. Permite la rotación, la compresión, la eliminación y el envío automáticos de los archivos de registro. Cada archivo de registro se puede administrar diariamente, semanalmente, mensualmente o cuando el archivo de registro supera un tamaño especificado.

Para obtener más información, vea una de las siguientes opciones:

* [Cómo: El tutorial de comando de rotación de registros definitivo con diez ejemplos](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [Intercambio de pila](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` página de comando man](https://linuxconfig.org/logrotate-8-manual-page)

>[!AVAILABILITY]
>
>La siguiente información de disponibilidad se aplica a los proyectos de Adobe Commerce en infraestructura en la nube:
>
>* Los entornos de inicio no tienen rotación de registro.
>
>* No se puede configurar la rotación de registros en entornos Pro Integration. Debe implementar una solución o script personalizado y [configurar su cron](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property) para ejecutar el script según sea necesario.

### Configure las reglas iptables para permitir que varios servicios se comuniquen

Tanto si tiene un servidor como si tiene varios, debe abrir puertos en el cortafuegos para permitir que los servicios se comuniquen. Por ejemplo, si utiliza el motor de búsqueda de Solr con Adobe Commerce, debe habilitarlo para que se comunique con el servidor web. Si tiene varios nodos web, debe habilitarlos para que se comuniquen entre sí.

Más información:

* Ubuntu: [página de documentación de Ubuntu](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [Procedimientos de CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).

### Reglas de seguridad mejorada de Linux (SELinux)

No tenemos una recomendación para si usa SELinux; sin embargo, si lo usa, debe configurar los servicios para comunicarse entre sí de manera similar a configurar iptables.

Más información:

* Ubuntu: [manual de Debian](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [wiki de CentOS](https://wiki.centos.org/HowTos/SELinux)

### Configurar un servidor de correo electrónico

Adobe Commerce requiere un servidor de correo electrónico. No recomendamos un servidor en particular, pero puede probar cualquiera de los siguientes métodos:

* Postfijo para CentOS ([tutorial de Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [documentación de CentOS](https://www.centos.org))
* Postfijo para Ubuntu ([tutorial de Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [documentación de Ubuntu](https://help.ubuntu.com/community/MailServer))

### Refine el motor de búsqueda para obtener un rendimiento mejorado:

Se requiere Elasticsearch o OpenSearch para todas las instalaciones a partir de la versión 2.4.0.

* [Instalación y configuración del motor de búsqueda](../../configuration/search/overview-search.md)

### Configuración de una cola de mensajes

Desde la versión 2.3.0, Adobe Commerce ha incluido la funcionalidad de cola de mensajes. En versiones anteriores, solo está disponible para Adobe Commerce.

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Configuración solo para Adobe Commerce

Solo puede configurar lo siguiente si utiliza Adobe Commerce:

* [Dividir bases de datos para cierres de compra, administración de pedidos y otras tablas de base de datos](../../configuration/storage/multi-master.md)
