---
title: Requisitos del sistema
description: Obtenga información sobre las dependencias de software y los requisitos del sistema para Adobe Commerce. Consulte las configuraciones probadas para comprobar la compatibilidad con el entorno de implementación.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
last-update: 2026-09-18
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 2456f0e28fa24e23eb7692a905c708007a00bd96
workflow-type: tm+mt
source-wordcount: '1614'
ht-degree: 0%
---
# Requisitos del sistema

La siguiente información resume las dependencias y servicios de software probados para Adobe Commerce.

Las dependencias de software para Adobe Commerce en la infraestructura de la nube difieren de las de las implementaciones locales. Adobe determina las versiones de servicio compatibles y la compatibilidad en función de los servicios probados e implementados en entornos de nube alojados. Estas versiones a veces difieren de las admitidas para implementaciones locales.

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

La [plantilla de Commerce en la nube](https://github.com/magento/magento-cloud) proporciona una configuración predeterminada para los servicios compatibles con la última versión de Commerce en cada línea de versión.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

El archivo [`services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml) define los servicios y las versiones predeterminados.
Consulte [Configurar servicios](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) en la guía de *Commerce en infraestructura en la nube*.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0 llegó al fin del soporte técnico (EOS) el 30 de abril de 2026.**
Después de esta fecha, Adobe Commerce 2.4.7, 2.4.6, 2.4.5 y 2.4.4 no proporcionan compatibilidad ni soporte para las versiones de MySQL publicadas después de MySQL 8.0.
Adobe no valida ni admite las versiones principales más recientes de MySQL para estas versiones de Commerce.
Si ejecuta las versiones locales de Adobe Commerce 2.4.7, 2.4.6, 2.4.5 o 2.4.4, Adobe recomienda migrar los servidores de bases de datos a una versión MariaDB compatible.

Los clientes de Adobe Commerce en la nube deben mantener las dependencias de plataforma de las versiones compatibles. Ver [dependencias de plataforma](../release/lifecycle-policy.md#platform-dependencies) en la directiva de ciclo vital.

**Elasticsearch 7.17 llegó al fin de la compatibilidad (EOS) el 15 de enero de 2026.**
Después de esta fecha, Adobe Commerce 2.4.6, 2.4.5 y 2.4.4 no proporcionan compatibilidad ni compatibilidad con las versiones de Elasticsearch publicadas después de Elasticsearch 7.
Adobe no valida ni admite las versiones principales más recientes de Elasticsearch para estas versiones de Commerce.
Si ejecuta las versiones locales de Adobe Commerce 2.4.6, 2.4.5 o 2.4.4, Adobe recomienda migrar su infraestructura de búsqueda a una versión de OpenSearch compatible.

>[!ENDTABS]

## Requisitos del sistema para la versión de Commerce 2.4.10-alpha

>[!BEGINTABS]

>[!TAB Commerce en la nube]

{{$include /help/_includes/templated/cloud-requirements-table-alpha.md}}

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table-alpha.md}}

>[!ENDTABS]

## Requisitos del sistema para versiones anteriores de Commerce

En las tablas siguientes se enumeran los requisitos del sistema para las versiones de Adobe Commerce, incluidas las de compatibilidad ampliada. Utilice estas tablas solo como referencia. Adobe no recomienda el uso de versiones no compatibles de dependencias de software. Antes de que el Soporte de Adobe investigue, solucione problemas o valide el comportamiento informado, debe alinear su entorno con una configuración admitida.

>[!NOTE]
>
>Adobe Commerce 2.4.6 cuenta con [soporte extendido](../release/lifecycle-policy.md#extended-support) hasta el **30 de agosto de 2027**, seguido de un [período de transición solo de seguridad](../release/lifecycle-policy.md#security-only-transitional-period) hasta el **31 de mayo de 2028**. Estas provisiones solo están disponibles para los clientes de Adobe Commerce. No amplían la compatibilidad con dependencias de terceros como MySQL.
>
>Si ejecuta Adobe Commerce en la nube, debe actualizar a una versión compatible o migrar a [!DNL Adobe Commerce as a Cloud Service] antes del **1 de junio de 2028** [requisitos de seguridad y plazos](../release/security-enforcement-policy.md). Consulte la tabla [fechas de fin de soporte](../release/lifecycle-policy.md#end-of-support-dates) para ver las fechas completas del ciclo vital.
>
>La tabla está contraída para minimizar la longitud de este artículo. Seleccione el encabezado para expandirlo.

+++Requisitos para versiones anteriores

>[!BEGINTABS]

>[!TAB Commerce en la nube]

La [plantilla de Commerce en la nube](https://github.com/magento/magento-cloud) proporciona una configuración predeterminada para los servicios compatibles con una versión específica de Commerce.

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

El archivo [`services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml) define los servicios y las versiones predeterminados.
Consulte [Configurar servicios](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) en la guía de *Commerce en infraestructura en la nube*.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**MySQL 8.0 llegó al fin del soporte técnico (EOS) el 30 de abril de 2026.**
Después de esta fecha, Adobe Commerce 2.4.7, 2.4.6, 2.4.5 y 2.4.4 no proporcionan compatibilidad ni soporte para las versiones de MySQL publicadas después de MySQL 8.0.
Adobe no valida ni admite las versiones principales más recientes de MySQL para estas versiones de Commerce.
Si ejecuta las versiones locales de Adobe Commerce 2.4.7, 2.4.6, 2.4.5 o 2.4.4, Adobe recomienda migrar los servidores de bases de datos a una versión MariaDB compatible.

Los clientes de Adobe Commerce en la nube deben mantener las dependencias de plataforma de las versiones compatibles. Ver [dependencias de plataforma](../release/lifecycle-policy.md#platform-dependencies) en la directiva de ciclo vital.

**Elasticsearch 7.17 llegó al fin de la compatibilidad (EOS) el 15 de enero de 2026.**
Después de esta fecha, Adobe Commerce 2.4.6, 2.4.5 y 2.4.4 no proporcionan compatibilidad ni compatibilidad con las versiones de Elasticsearch publicadas después de Elasticsearch 7.
Adobe no valida ni admite las versiones principales más recientes de Elasticsearch para estas versiones de Commerce.
Si ejecuta las versiones locales de Adobe Commerce 2.4.6, 2.4.5 o 2.4.4, Adobe recomienda migrar su infraestructura de búsqueda a una versión de OpenSearch compatible.

>[!ENDTABS]

+++

## Configuración de PHP

Configure las opciones de PHP, como `memory_limit`, para evitar problemas comunes al usar Adobe Commerce. Consulte [Configuración de PHP requerida](prerequisites/php-settings.md).

Para obtener instrucciones de configuración de Cloud, consulte [Configuración de PHP](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings) en la guía de *Commerce en infraestructura en la nube*.

### OPcache de PHP

Adobe recomienda comprobar que [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) está habilitado para mejorar el rendimiento. Muchas distribuciones PHP habilitan OPcache.

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
>Para las extensiones PHP en la infraestructura en la nube, consulte [Habilitar extensiones PHP](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions) en la guía de _Commerce en la infraestructura en la nube_.

>[!BEGINTABS]

>[!TAB Commerce en la nube]

La siguiente tabla muestra las extensiones PHP compatibles al implementar Adobe Commerce en la plataforma Cloud.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce local]

{{$include /help/_includes/templated/php-extensions.md}}

Consulte la [documentación oficial de PHP](https://www.php.net/manual/en/extensions.php) para obtener detalles sobre la instalación.

>[!ENDTABS]

## Otros requisitos de software

En esta sección se describe la compatibilidad con todos los demás tipos de software opcional y necesario.

>[!NOTE]
>
>Los siguientes requisitos se aplican a la última versión del parche 2.4.x de Adobe Commerce. Si es relevante, se proporciona orientación sobre la infraestructura de Commerce en la nube.

### Navegadores

Adobe Commerce es compatible con las versiones principales más recientes y anteriores de los siguientes exploradores para la tienda y el administrador, excepto cuando se indique lo siguiente:

- Microsoft Edge
- Firefox (cualquier sistema operativo)
- Chrome (cualquier sistema operativo)
- Safari (solo macOS)
- Safari para iOS (solo tienda)
- Chrome para Android (solo tienda)

### Servidor de correo

Agente de transferencia de correo (MTA) o un servidor SMTP. La infraestructura de Commerce en la nube usa el [servicio de correo electrónico SendGrid](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid).

### Memoria

La actualización de aplicaciones y extensiones desde Commerce Marketplace y otras fuentes puede requerir hasta 2 GB de RAM. Si tu sistema tiene menos de 2 GB de RAM, crea un [archivo de intercambio](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade). Sin un archivo de intercambio, es posible que la actualización falle.

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

Para Commerce sobre la infraestructura en la nube, consulte [Configuración rápida](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration) en la guía de *Commerce sobre la infraestructura en la nube*.

### Xdebug

Solo para entornos de desarrollo de Adobe Commerce, use [php_xdebug 2.5.x](https://xdebug.org/download) o posterior. Xdebug puede afectar negativamente al rendimiento.

Para Adobe Commerce en la nube, consulte [Configuración de Xdebug](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/debug) en la guía de *Commerce en infraestructura en la nube*.

>[!NOTE]
>
>Un problema conocido con Xdebug puede afectar a las instalaciones de Adobe Commerce o al acceso a la tienda o al administrador después de la instalación. Ver [Problema conocido que afecta a la instalación de `xdebug`](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation) en la _Base de conocimiento de soporte técnico de Commerce_.

<!-- Last updated from includes: 2026-10-13 09:11:06 -->
