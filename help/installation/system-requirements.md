---
title: Requisitos del sistema
description: Obtenga información sobre las dependencias de software y los requisitos del sistema para Adobe Commerce. Descubra las configuraciones probadas para garantizar la compatibilidad con el entorno de implementación.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 8b1a202fde89ab05626194aff010111577ef6993
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---

# Requisitos del sistema

A continuación se resumen las dependencias y servicios de software probados para Adobe Commerce.

Existen algunas diferencias en las dependencias para Commerce en la nube. La compatibilidad y la versión de los servicios para Adobe Commerce en la nube están determinadas por los servicios probados e implementados en los entornos de nube alojados y, a veces, difieren de las versiones admitidas por las implementaciones locales de Adobe Commerce. Por ejemplo, Elasticsearch 7.17 es compatible con Commerce 2.4.4 para implementaciones locales, pero OpenSearch 1 es compatible con Adobe Commerce 2.4.4 en la nube.

>[!NOTE]
>
>Los requisitos del sistema solo se aplican a las versiones publicadas de Adobe Commerce. No se incluyen las versiones de Beta o de acceso anticipado. Consulte las [notas de la versión](../release/release-notes/overview.md) para obtener más información sobre las últimas versiones de Adobe Commerce.

Las siguientes tablas muestran versiones de dependencias de software de terceros que Adobe ha probado con versiones específicas de Adobe Commerce.

Adobe solo admite la combinación de requisitos del sistema que se describen en las tablas siguientes. Por ejemplo, 2.4.5 se ha probado completamente con MariaDB 10.4. Adobe recomienda actualizar a MariaDB 10.4 antes de actualizar a 2.4.5.

Para garantizar un proceso de actualización sin problemas y evitar errores de implementación, Adobe recomienda actualizar las versiones de RabbitMQ gradualmente. Por ejemplo, al actualizar de la versión 3.8 a la 4.1, primero debe actualizar de la 3.8 a la 3.9, después de la 3.9 a la 3.10, y así sucesivamente. Solo después de llegar a la versión 3.13 debe continuar con la actualización a la versión 4.1.

>[!BEGINTABS]

>[!TAB Commerce en la nube]

La [plantilla de Commerce en la nube](https://github.com/magento/magento-cloud) proporciona una configuración predeterminada para los servicios compatibles con una versión específica de Commerce.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Los servicios y las versiones se definen en [el archivo `services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). A continuación se muestra la configuración de servicio predeterminada para Commerce 2.4.6 en infraestructura en la nube:

```yaml
mysql:
    type: mysql:10.6
    disk: 5120

redis:
    type: redis:7.0

opensearch:
    type: opensearch:2
    disk: 1024
```

Consulte [Configurar servicios](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html?lang=es) en la guía de _Commerce en infraestructura en la nube_.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## Configuración de PHP

Hay ciertas opciones de configuración de PHP, como la configuración de `memory_limit`, que pueden ayudarle a evitar problemas comunes al usar Adobe Commerce. Consulte [Configuración de PHP requerida](prerequisites/php-settings.md).

Para obtener instrucciones de configuración de Cloud, consulte [Configuración de PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html?lang=es) en la guía de _Commerce en infraestructura en la nube_.

### OPcache de PHP

Se recomienda verificar que [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) está habilitado por motivos de rendimiento. OPcache está habilitado en muchas distribuciones PHP. La extensión `opcache` está instalada de manera predeterminada en Commerce en la infraestructura de la nube.

Para obtener información local, compruebe que PHP OPcache está instalado. Consulte [Configuración de PHP](prerequisites/php-settings.md). O para obtener instrucciones específicas sobre la configuración de rendimiento, consulte las recomendaciones de software para [configuración de PHP](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html?lang=es#php-settings) en la guía de _Prácticas recomendadas de rendimiento_.

Si debe instalar OPcache por separado, consulte la [documentación de OPcache de PHP](https://www.php.net/manual/en/opcache.setup.php).

### Control de procesos PHP

{{php-process-control}}

### PHPUnit

PHPUnit v9 (como herramienta de línea de comandos).

### Extensiones de PHP

Las [instrucciones de instalación de PHP](prerequisites/php-settings.md) incluyen un paso para instalar estas extensiones.

>[!TIP]
>
>Para las extensiones PHP en la infraestructura en la nube, consulte [Habilitar extensiones PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html?lang=es#enable-extensions) en la guía de _Commerce en la infraestructura en la nube_.

>[!BEGINTABS]

>[!TAB Commerce en la nube]

La siguiente tabla muestra las extensiones PHP compatibles al implementar Adobe Commerce en la plataforma Cloud.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce local]

{{$include /help/_includes/templated/php-extensions.md}}

Consulte [documentación oficial de PHP](https://www.php.net/manual/en/extensions.php) para obtener detalles de instalación.

>[!ENDTABS]

## Varios

En esta sección se describe la compatibilidad con todos los demás tipos de software opcional y necesario.

>[!NOTE]
>
>Los siguientes requisitos se aplican a la última versión del parche 2.4.x de Adobe Commerce. Si es relevante, se proporciona orientación sobre la infraestructura de Commerce en la nube.

### Navegadores

Tienda y administrador:

- Microsoft Edge (versión principal más reciente y anterior)
- Firefox (versión principal más reciente y anterior; cualquier sistema operativo)
- Chrome (última versión y anterior; cualquier sistema operativo)
- Safari (versión principal más reciente y anterior; solo macOS)
- Safari para iOS (versión principal más reciente y anterior, para tienda)
- Chrome para Android (versión principal más reciente y anterior, para tienda)

### Servidor de correo

Agente de transferencia de correo (MTA) o un servidor SMTP. La infraestructura de Commerce en la nube usa el [servicio de correo electrónico SendGrid](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html?lang=es).

### Memoria

La actualización de las aplicaciones y extensiones que obtiene de Commerce Marketplace y otras fuentes puede requerir hasta 2 GB de RAM. Si usa un sistema con menos de 2 GB de RAM, cree un [archivo de intercambio](https://support.magento.com/hc/en-us/articles/360032980432); de lo contrario, podría producirse un error en la actualización.

### Sistemas operativos (Linux x86-64)

Distribuciones de Linux, como RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian y similares.

Microsoft Windows y macOS **no son compatibles**.

Adobe Commerce requiere las siguientes herramientas del sistema para algunas operaciones:

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gzip.org/)
- [[!DNL lsof]](https://linux.die.net/man/8/lsof)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [[!DNL nice]](https://linux.die.net/man/1/nice)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://linux.die.net/man/1/tar)

### SSL

- Se requiere un certificado de seguridad válido para HTTPS.
- No se admiten certificados SSL firmados automáticamente.
- Requisito de seguridad de la capa de transporte (TLS): PayPal y `repo.magento.com` requieren TLS 1.2 o posterior.

Para Commerce sobre la infraestructura en la nube, consulte [Configuración rápida](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=es) en la guía de _Commerce sobre la infraestructura en la nube_.

### Xdebug

Para Adobe Commerce, use [php_xdebug 2.5.x](https://xdebug.org/download) o posterior (solo para entornos de desarrollo; puede tener un efecto adverso en el rendimiento).

Para Adobe Commerce en la nube, consulte [Configuración de Xdebug](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html?lang=es) en la guía de _Commerce en infraestructura en la nube_.

>[!NOTE]
>
>Hay un problema conocido con `xdebug` que puede afectar las instalaciones de Adobe Commerce o el acceso a la tienda o al administrador después de la instalación. Ver [Problema conocido que afecta a la instalación de `xdebug`](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html?lang=es) en la _Base de conocimiento de soporte técnico de Commerce_.


<!-- Last updated from includes: 2025-10-09 19:48:53 -->
