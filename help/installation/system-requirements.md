---
title: Requisitos del sistema
description: Obtenga información sobre las dependencias de software y los requisitos del sistema para Adobe Commerce. Consulte las configuraciones probadas para comprobar la compatibilidad con el entorno de implementación.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: e77a19ce01fb0dd650aee3e8ec5f86375b429451
workflow-type: tm+mt
source-wordcount: '1249'
ht-degree: 0%

---

# Requisitos del sistema

La siguiente información resume las dependencias y servicios de software probados para Adobe Commerce.

Existen algunas diferencias en las dependencias para Commerce en la nube. La compatibilidad y la versión de los servicios para Adobe Commerce en la nube están determinadas por los servicios probados e implementados en los entornos de nube alojados y, a veces, difieren de las versiones admitidas por las implementaciones locales de Adobe Commerce.

>[!IMPORTANT]
>
>Las tablas de requisitos del sistema enumeran las versiones de Adobe Commerce a las que se aplican, incluidas las versiones etiquetadas como beta o acceso anticipado.
>Consulte las [notas de la versión](../release/release-notes/overview.md) para ver las últimas versiones publicadas de Commerce.
>
>Cuando las versiones del servicio no coinciden con la configuración admitida para la versión de Commerce, el comportamiento puede diferir de lo que Adobe puede reproducir en las pruebas. El Soporte de Adobe puede pedirle que alinee su entorno con una configuración admitida antes de investigar, solucionar problemas o validar el comportamiento del que se ha informado. Después de alinear el entorno, el Soporte de Adobe puede continuar con la investigación.

Las siguientes tablas muestran versiones de dependencias de software de terceros que Adobe ha probado con versiones específicas de Adobe Commerce.

Adobe solo admite las combinaciones de requisitos del sistema enumeradas en las tablas siguientes. Adobe no valida ni admite configuraciones que no coincidan con una combinación de la lista. Por ejemplo, Adobe Commerce 2.4.9 se prueba con MariaDB 12.3. Actualice a MariaDB 12.3 antes de actualizar a 2.4.9.

## Requisitos del sistema para las últimas versiones de Commerce

Las siguientes tablas resumen los requisitos del sistema para la última versión de todas las versiones de Commerce compatibles. Adobe recomienda que todos los clientes actualicen a estas versiones.

>[!BEGINTABS]

>[!TAB Commerce en la nube]

La [plantilla de Commerce en la nube](https://github.com/magento/magento-cloud) proporciona una configuración predeterminada para los servicios compatibles con una versión específica de Commerce.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

**<sup>1</sup>Compatibilidad entre MariaDB 12.3 y Adobe Commerce 2.4.9**
La compatibilidad entre MariaDB 12.3 y Adobe Commerce 2.4.9 se confirmará tras el lanzamiento oficial de MariaDB 12.3, previsto en el periodo de tiempo de mayo a junio.

Para la configuración predeterminada, los servicios y las versiones se definen en [el archivo `services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml).
Para obtener más información, consulte [Configuración de servicios](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) en la guía de *Commerce en infraestructura en la nube*.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0 llegó al fin del soporte técnico (EOS) el 30 de abril de 2026.**
Después de esta fecha, Adobe Commerce 2.4.7, 2.4.6, 2.4.5 y 2.4.4 no proporcionará compatibilidad ni
compatibilidad con cualquier versión de MySQL lanzada después de MySQL 8.0. Adobe no
validar o proporcionar compatibilidad con las versiones principales más recientes de MySQL en este Adobe
Línea de versión de Commerce.
Todos los clientes locales de Adobe Commerce que ejecutan las versiones 2.4.7, 2.4.6, 2.4.5 y 2.4.4 tienen una
se aconseja migrar sus servidores de base de datos a una versión de MariaDB compatible.

**Elasticsearch 7.17 llegó al fin de la compatibilidad (EOS) el 15 de enero de 2026.**
Después de esta fecha, Adobe Commerce 2.4.6, 2.4.5 y 2.4.4 no proporcionará compatibilidad o
compatibilidad con cualquier versión de Elasticsearch lanzada después de Elasticsearch 7. Adobe no
validar o proporcionar compatibilidad con las versiones principales más recientes de Elasticsearch en este Adobe
Línea de versión de Commerce.
Todos los clientes locales de Adobe Commerce que ejecutan las versiones 2.4.6, 2.4.5 y 2.4.4 tienen una
se aconseja migrar su infraestructura de búsqueda a una versión compatible de OpenSearch.

>[!ENDTABS]

## Requisitos del sistema para versiones anteriores de Commerce

En las tablas siguientes se enumeran los requisitos del sistema para las versiones de Adobe Commerce, incluidas las que son compatibles con versiones ampliadas. Estas tablas se proporcionan solo con fines de referencia. Adobe no recomienda el uso de versiones no admitidas de dependencias de software y la Asistencia técnica requiere que alinee su entorno con una configuración admitida para que podamos investigar, solucionar problemas o validar el comportamiento notificado.

>[!NOTE]
>
>La tabla está contraída para minimizar la longitud de este artículo. Seleccione el encabezado para expandirlo.

+++Requisitos para versiones anteriores

>[!BEGINTABS]

>[!TAB Commerce en la nube]

La [plantilla de Commerce en la nube](https://github.com/magento/magento-cloud) proporciona una configuración predeterminada para los servicios compatibles con una versión específica de Commerce.

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

Para la configuración predeterminada, los servicios y las versiones se definen en [el archivo `services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml).
Para obtener más información, consulte [Configuración de servicios](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) en la guía de *Commerce en infraestructura en la nube*.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**MySQL 8.0 llegó al fin del soporte técnico (EOS) el 30 de abril de 2026.**
Después de esta fecha, Adobe Commerce 2.4.7, 2.4.6, 2.4.5 y 2.4.4 no proporcionará compatibilidad ni
compatibilidad con cualquier versión de MySQL lanzada después de MySQL 8.0. Adobe no
validar o proporcionar compatibilidad con las versiones principales más recientes de MySQL en este Adobe
Línea de versión de Commerce.
Todos los clientes locales de Adobe Commerce que ejecutan las versiones 2.4.7, 2.4.6, 2.4.5 y 2.4.4 tienen una
se aconseja migrar sus servidores de base de datos a una versión de MariaDB compatible.

**Elasticsearch 7.17 llegó al fin de la compatibilidad (EOS) el 15 de enero de 2026.**
Después de esta fecha, Adobe Commerce 2.4.6, 2.4.5 y 2.4.4 no proporcionará compatibilidad o
compatibilidad con cualquier versión de Elasticsearch lanzada después de Elasticsearch 7. Adobe no
validar o proporcionar compatibilidad con las versiones principales más recientes de Elasticsearch en este Adobe
Línea de versión de Commerce.
Todos los clientes locales de Adobe Commerce que ejecutan las versiones 2.4.6, 2.4.5 y 2.4.4 tienen una
se aconseja migrar su infraestructura de búsqueda a una versión compatible de OpenSearch.

>[!ENDTABS]

+++

## Configuración de PHP

Hay ciertas opciones de configuración de PHP, como la configuración de `memory_limit`, que pueden ayudarle a evitar problemas comunes al usar Adobe Commerce. Consulte [Configuración de PHP requerida](prerequisites/php-settings.md).

Para obtener instrucciones de configuración de Cloud, consulte [Configuración de PHP](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/app/php-settings) en la guía de *Commerce en infraestructura en la nube*.

### OPcache de PHP

Adobe recomienda comprobar que [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) está habilitado por motivos de rendimiento. OPcache está habilitado en muchas distribuciones PHP.

- **Para implementaciones de infraestructura de Adobe Commerce en la nube**, la extensión `opcache` se instala de manera predeterminada.
- **Para implementaciones locales de Adobe Commerce:**
   - [Compruebe que la extensión PHP OPcache esté instalada](prerequisites/php-settings.md#verify-php-is-installed).
   - Para obtener instrucciones específicas sobre la configuración de rendimiento, consulte las recomendaciones de software para [configuración de PHP](../performance/software.md#php-settings) en la guía de *Prácticas recomendadas de rendimiento*.


Si debe instalar OPcache por separado, consulte la [documentación de OPcache de PHP](https://www.php.net/manual/en/opcache.setup.php).

### Control de procesos PHP

{{php-process-control}}

### PHPUnit

La versión principal de PHPUnit admitida depende de la versión de Adobe Commerce. Adobe prueba 2.4.9 con PHPUnit 12, 2.4.8-p5 con PHPUnit 10 y 2.4.7-p10 a 2.4.4-p18 con PHPUnit 9. Instale PHPUnit como herramienta de línea de comandos en la versión principal que coincida con las configuraciones probadas de Adobe para su versión.

### Extensiones de PHP

Las [instrucciones de instalación de PHP](prerequisites/php-settings.md) incluyen un paso para instalar estas extensiones.

>[!TIP]
>
>Para las extensiones PHP en la infraestructura en la nube, consulte [Habilitar extensiones PHP](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions) en la guía de _Commerce en la infraestructura en la nube_.

>[!BEGINTABS]

>[!TAB Commerce en la nube]

La siguiente tabla muestra las extensiones PHP compatibles al implementar Adobe Commerce en la plataforma Cloud.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce local]

{{$include /help/_includes/templated/php-extensions.md}}

Consulte [documentación oficial de PHP](https://www.php.net/manual/en/extensions.php) para obtener detalles de instalación.

>[!ENDTABS]

## Otros requisitos de software

En esta sección se describe la compatibilidad con todos los demás tipos de software opcional y necesario.

>[!NOTE]
>
>Los siguientes requisitos se aplican a la última versión del parche 2.4.x de Adobe Commerce. Si es relevante, se proporciona orientación sobre la infraestructura de Commerce en la nube.

### Navegadores

Tienda y administrador:

- Microsoft Edge (versión principal más reciente y anterior)
- Firefox (última versión y anterior en cualquier sistema operativo)
- Chrome (versión principal más reciente y anterior en cualquier sistema operativo)
- Safari (versión principal más reciente y anterior solo en macOS)
- Safari para iOS (versión principal más reciente y anterior de la tienda)
- Chrome para Android (versión principal más reciente y anterior de la tienda)

### Servidor de correo

Agente de transferencia de correo (MTA) o un servidor SMTP. La infraestructura de Commerce en la nube usa el [servicio de correo electrónico SendGrid](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/project/sendgrid).

### Memoria

La actualización de las aplicaciones y extensiones que obtiene de Commerce Marketplace y otras fuentes puede requerir hasta 2 GB de RAM. Si usa un sistema con menos de 2 GB de RAM, cree un [archivo de intercambio](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade). De lo contrario, es posible que la actualización falle.

### Sistemas operativos (Linux x86-64)

Distribuciones de Linux, como Red Hat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian y similares.

Microsoft Windows y macOS **no son compatibles**.

Adobe Commerce requiere las siguientes herramientas del sistema para algunas operaciones:

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gnu.org/software/gzip/manual/gzip.html)
- [[!DNL lsof]](https://lsof.readthedocs.io/en/stable/manpage/)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.4/en/mysqldump.html)
- [[!DNL nice]](https://www.gnu.org/s/coreutils/manual/html_node/nice-invocation.html)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://www.gnu.org/software/tar/manual/tar.html)

### SSL

- Se requiere un certificado de seguridad válido para HTTPS.
- No se admiten certificados SSL firmados automáticamente.
- Requisito de seguridad de la capa de transporte (TLS): PayPal y `repo.magento.com` requieren TLS 1.2 o posterior.

Para Commerce sobre la infraestructura en la nube, consulte [Configuración rápida](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration) en la guía de *Commerce sobre la infraestructura en la nube*.

### Xdebug

Para Adobe Commerce, use [php_xdebug 2.5.x](https://xdebug.org/download) o posterior (solo para entornos de desarrollo; puede tener un efecto adverso en el rendimiento).

Para Adobe Commerce en la nube, consulte [Configuración de Xdebug](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/test/debug) en la guía de *Commerce en infraestructura en la nube*.

>[!NOTE]
>
>Hay un problema conocido con `xdebug` que puede afectar las instalaciones de Adobe Commerce o el acceso a la tienda o al administrador después de la instalación. Ver [Problema conocido que afecta a la instalación de `xdebug`](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation) en la _Base de conocimiento de soporte técnico de Commerce_.

<!-- Last updated from includes: 2026-06-01 15:26:19 -->
