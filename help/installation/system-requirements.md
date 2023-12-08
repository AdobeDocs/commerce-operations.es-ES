---
title: Requisitos del sistema
description: Utilice esta referencia para identificar las dependencias de software necesarias que se han probado con las versiones de Adobe Commerce y Magento Open Source.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 8b9e4de2799532e4654fce63d856c2d301025f09
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 0%

---

# Requisitos del sistema

A continuación se resumen las dependencias y servicios de software probados para Adobe Commerce y Magento Open Source.

Existen algunas diferencias en las dependencias para Commerce en la infraestructura en la nube. La compatibilidad y la versión de los servicios para Adobe Commerce en la infraestructura en la nube están determinadas por los servicios probados e implementados en los entornos en la nube alojados y, a veces, difieren de las versiones admitidas por las implementaciones locales de Adobe Commerce. Por ejemplo, el Elasticsearch 7.17 es compatible con Commerce 2.4.4 para implementaciones on-premise, pero OpenSearch 1.2 es compatible con Commerce 2.4.4 en infraestructura en la nube.

Las siguientes tablas muestran versiones de dependencias de software de terceros que Adobe ha probado con versiones específicas de Adobe Commerce y de Magento Open Source.

El Adobe solo admite la combinación de requisitos del sistema que se describen en las tablas siguientes. Por ejemplo, 2.4.5 se ha probado completamente con MariaDB 10.4. El Adobe recomienda actualizar a MariaDB 10.4 antes de actualizar a 2.4.5.

>[!BEGINTABS]

>[!TAB Commerce en la nube]

El [Plantilla de Commerce on Cloud](https://github.com/magento/magento-cloud) proporciona una configuración predeterminada para servicios compatibles con una versión específica de Commerce.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Los servicios y las versiones se definen en [el `services.yaml` archivo](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). A continuación se muestra la configuración de servicio predeterminada para Commerce 2.4.6 en la infraestructura en la nube:

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

Consulte [Configurar servicios](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) en el _Commerce en infraestructura en la nube_ guía.

>[!TAB Commerce local]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## Configuración de PHP

Hay ciertas configuraciones de PHP, como la `memory_limit` , que puede ayudarle a evitar problemas comunes al utilizar Adobe Commerce y Magento Open Source. Consulte [Configuración de PHP requerida](prerequisites/php-settings.md).

Para obtener instrucciones de configuración de Cloud, consulte [Configuración de PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) en el _Commerce en infraestructura en la nube_ guía.

### OPcache de PHP

Se recomienda verificar que [OPcache de PHP](https://www.php.net/manual/en/intro.opcache.php) está habilitado por motivos de rendimiento. OPcache está habilitado en muchas distribuciones PHP. El `opcache` La extensión de se instala de forma predeterminada en la infraestructura de Commerce en la nube.

Para obtener información local, compruebe que está instalado el OPcache de PHP, consulte [Configuración de PHP](prerequisites/php-settings.md). O para obtener instrucciones específicas sobre la configuración de rendimiento, consulte las recomendaciones de software para [Configuración de PHP](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) en el _Prácticas recomendadas de rendimiento_ guía.

Si debe instalar OPcache por separado, consulte la [Documentación de PHP OPcache](https://www.php.net/manual/en/opcache.setup.php).

### Control de procesos PHP

{{php-process-control}}

### PHPUnit

PHPUnit (como herramienta de línea de comandos) 9.0.0

### Extensiones de PHP

El [Instrucciones de instalación de PHP](prerequisites/php-settings.md) incluya un paso para instalar estas extensiones.

>[!TIP]
>
>Para ver las extensiones PHP en la infraestructura de Cloud, consulte [Habilitar extensiones PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) en el _Commerce en infraestructura en la nube_ guía.

>[!BEGINTABS]

>[!TAB Commerce en la nube]

La siguiente tabla muestra las extensiones PHP compatibles al implementar Adobe Commerce en la plataforma Cloud.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce local]

{{$include /help/_includes/templated/php-extensions.md}}

Consulte [documentación oficial de PHP](https://www.php.net/manual/en/extensions.php) para obtener más información sobre la instalación.

>[!ENDTABS]

## Varios

En esta sección se describe la compatibilidad con todos los demás tipos de software opcional y necesario.

>[!NOTE]
>
>Los siguientes requisitos se aplican a la última versión de parches de 2.4.x de Adobe Commerce y Magento Open Source. Cuando es relevante, se proporciona orientación sobre la infraestructura de Commerce en la nube.

### Navegadores

Tienda y administrador:

- Microsoft Edge (versión principal más reciente y anterior)
- Firefox (versión principal más reciente y anterior; cualquier sistema operativo)
- Chrome (última versión principal y anterior; cualquier sistema operativo)
- Safari (versión principal más reciente y anterior; solo macOS)
- Safari Mobile para iPad 2, iPad Mini, iPad con pantalla Retina (iOS 12 o posterior), para tienda de escritorio
- Safari Mobile para iPhone 6 o posterior; iOS 12 o posterior, para tienda móvil
- Chrome para móviles (versión principal más reciente y anterior) [Android™ 4 o posterior] para tienda móvil)

### Servidor de correo

Agente de transferencia de correo (MTA) o un servidor SMTP. La infraestructura de Commerce en Cloud utiliza [Servicio de correo electrónico SendGrid](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### Memoria

La actualización de las aplicaciones y extensiones que obtiene del Commerce Marketplace y de otras fuentes puede requerir hasta 2 GB de RAM. Si utiliza un sistema con menos de 2 GB de RAM, cree un [archivo de intercambio](https://support.magento.com/hc/en-us/articles/360032980432); de lo contrario, es posible que la actualización falle.

### Sistemas operativos (Linux x86-64)

Distribuciones de Linux, como RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian y similares. Microsoft Windows y macOS no son compatibles.

Adobe Commerce y Magento Open Source requieren las siguientes herramientas del sistema para algunas operaciones:

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
- Requisito de seguridad de la capa de transporte (TLS): PayPal y `repo.magento.com` ambos requieren TLS 1.2 o posterior.

Para Commerce en la infraestructura en la nube, consulte [Configuración rápida](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) en el _Commerce en infraestructura en la nube_ guía.

### Xdebug

Para Adobe Commerce y Magento Open Source, utilice [php_xdebug 2.5.x](https://xdebug.org/download) o posterior (solo entornos de desarrollo; puede tener un efecto adverso en el rendimiento).

Para Adobe Commerce en la nube, consulte [Configurar Xdebug](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) en el _Commerce en infraestructura en la nube_ guía.

>[!NOTE]
>
>Hay un problema conocido con `xdebug` que pueden afectar a las instalaciones de Adobe Commerce o de Magento Open Source o al acceso a la tienda o al administrador después de la instalación. Consulte [Problema conocido que afecta a `xdebug` instalación](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) en el _Base de conocimiento de asistencia de Commerce_.
