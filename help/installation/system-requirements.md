---
title: Requisitos del sistema
description: Obtenga información sobre las dependencias de software y los requisitos del sistema para Adobe Commerce. Descubra las configuraciones probadas para garantizar la compatibilidad con el entorno de implementación.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: e0905f357c5ab84b30304eeaad00d9ae4ec0c168
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---

# Requisitos del sistema

A continuación se resumen las dependencias y servicios de software probados para Adobe Commerce.

Existen algunas diferencias en las dependencias para Commerce en la nube. La compatibilidad y la versión de los servicios para Adobe Commerce en la nube están determinadas por los servicios probados e implementados en los entornos de nube alojados y, a veces, difieren de las versiones admitidas por las implementaciones locales de Adobe Commerce. Por ejemplo, Elasticsearch 7.17 es compatible con Commerce 2.4.4 para implementaciones locales, pero OpenSearch 1 es compatible con Adobe Commerce 2.4.4 en la nube.

>[!NOTE]
>
>Las tablas de requisitos del sistema identifican las versiones de Adobe Commerce específicas incluidas, incluidas las versiones beta o de acceso anticipado etiquetadas explícitamente. Consulte las [notas de la versión](../release/release-notes/overview.md) para obtener más información sobre las últimas versiones publicadas de Adobe Commerce.
>
>Las discrepancias en la versión del servicio respecto a la versión de Commerce pueden introducir un comportamiento que no se pueda reproducir en los entornos admitidos. In these cases, Support may request that you align the environment to a supported configuration (for example, upgrade or downgrade the service version) before we can investigate, troubleshoot, or validate the reported behavior. Una vez que las versiones están alineadas, el soporte técnico puede continuar con la investigación.

Las siguientes tablas muestran versiones de dependencias de software de terceros que Adobe ha probado con versiones específicas de Adobe Commerce.

Adobe only supports the combination of system requirements described in the following tables. Por ejemplo, 2.4.5 se ha probado completamente con MariaDB 10.4. Adobe recomienda actualizar a MariaDB 10.4 antes de actualizar a 2.4.5.

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

Consulte [Configurar servicios](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) en la guía de *Commerce en infraestructura en la nube*.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## Configuración de PHP

Hay ciertas opciones de configuración de PHP, como la configuración de `memory_limit`, que pueden ayudarle a evitar problemas comunes al usar Adobe Commerce. Consulte [Configuración de PHP requerida](prerequisites/php-settings.md).

Para obtener instrucciones de configuración de Cloud, consulte [Configuración de PHP](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/app/php-settings) en la guía de *Commerce en infraestructura en la nube*.

### OPcache de PHP

Adobe recomienda comprobar que [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) está habilitado por motivos de rendimiento. OPcache está habilitado en muchas distribuciones PHP.
- **Para implementaciones de infraestructura de Adobe Commerce en la nube**, la extensión `opcache` se instala de manera predeterminada.
- **For Adobe Commerce on-premises deployments:**
   - [Compruebe que la extensión PHP OPcache esté instalada](prerequisites/php-settings.md#verify-php-is-installed).
   - Para obtener instrucciones específicas sobre la configuración de rendimiento, consulte las recomendaciones de software para [configuración de PHP](../performance/software.md#php-settings) en la guía de *Prácticas recomendadas de rendimiento*.


Si debe instalar OPcache por separado, consulte la [documentación de OPcache de PHP](https://www.php.net/manual/en/opcache.setup.php).

### Control de procesos PHP

{{php-process-control}}

### PHPUnit

PHPUnit v9 (como herramienta de línea de comandos).

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

Agente de transferencia de correo (MTA) o un servidor SMTP. La infraestructura de Commerce en la nube usa el [servicio de correo electrónico SendGrid](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/project/sendgrid).

### Memoria

La actualización de las aplicaciones y extensiones que obtiene de Commerce Marketplace y otras fuentes puede requerir hasta 2 GB de RAM. Si usa un sistema con menos de 2 GB de RAM, cree un [archivo de intercambio](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade). De lo contrario, es posible que la actualización falle.

### Sistemas operativos (Linux x86-64)

Distribuciones de Linux, como RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian y similares.

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

For Adobe Commerce, use [php_xdebug 2.5.x](https://xdebug.org/download) or later (development environments only; can have an adverse effect on performance).

For Adobe Commerce on Cloud, see [Configure Xdebug](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/test/debug) in the *Commerce on Cloud Infrastructure* guide.

>[!NOTE]
>
>There is a known issue with `xdebug` that can affect Adobe Commerce installations or access to the storefront or Admin after installation. See [Known issue that affects `xdebug` installation](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation) in the _Commerce Support Knowledge Base_.


<!-- Last updated from includes: 2026-04-07 14:41:32 -->
