---
title: Requisitos del sistema
description: Utilice esta referencia para identificar las dependencias de software necesarias que se han probado con las versiones de Adobe Commerce y Magento Open Source.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# Requisitos del sistema

Esta tabla muestra las versiones de dependencias de software de terceros que Adobe ha probado con versiones específicas de Adobe Commerce y de Magento Open Source. El Adobe solo admite la combinación de requisitos del sistema que se describen en la siguiente tabla.

Por ejemplo, 2.4.5 se ha probado completamente con MariaDB 10.4. El Adobe recomienda actualizar a MariaDB 10.4 antes de actualizar a 2.4.5.

{{$include /help/_includes/templated/system-requirements-table.md}}

## Varios

En esta sección se describe la compatibilidad con todos los demás tipos de software opcional y necesario.

>[!NOTE]
>
>Los siguientes requisitos se aplican a la última versión de parches de 2.4.x de Adobe Commerce y Magento Open Source.

### Servidor de correo

Agente de transferencia de correo (MTA) o servidor SMTP

### Sistemas operativos (Linux x86-64)

Distribuciones de Linux, como RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian y similares. Microsoft Windows y macOS no son compatibles.

### Extensiones de PHP

>[!NOTE]
>
>El [Instrucciones de instalación de PHP](prerequisites/php-settings.md) incluya un paso para instalar estas extensiones.

{{$include /help/_includes/templated/php-extensions.md}}

Consulte [documentación oficial de PHP](https://php.net/manual/en/extensions.php) para obtener más información sobre la instalación.

### OPcache de PHP

Le recomendamos encarecidamente que compruebe que [OPcache de PHP](https://php.net/manual/en/intro.opcache.php) está habilitado por motivos de rendimiento. OPcache está habilitado en muchas distribuciones PHP. Para comprobar si está instalado, consulte nuestra [Documentación de PHP](prerequisites/php-settings.md).

Si debe instalarlo por separado, consulte la [Documentación de PHP OPcache](https://php.net/manual/en/opcache.setup.php).

### Configuración de PHP

Recomendamos ajustes de configuración de PHP específicos, como `memory_limit`, que puede evitar problemas comunes al utilizar Adobe Commerce y Magento Open Source.

Para obtener más información, consulte [Configuración de PHP requerida](prerequisites/php-settings.md).

### PHPUnit

PHPUnit (como herramienta de línea de comandos) 9.0.0

### RAM

La actualización de las aplicaciones y extensiones que obtiene del Commerce Marketplace y de otras fuentes puede requerir hasta 2 GB de RAM. Si utiliza un sistema con menos de 2 GB de RAM, le recomendamos que cree un [archivo de intercambio](https://support.magento.com/hc/en-us/articles/360032980432); de lo contrario, es posible que la actualización falle.

### Dependencias del sistema

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

### Navegadores admitidos

Tienda y administrador:

- Microsoft Edge (versión principal más reciente y anterior)
- Firefox (versión principal más reciente y anterior; cualquier sistema operativo)
- Chrome (última versión principal y anterior; cualquier sistema operativo)
- Safari (versión principal más reciente y anterior; solo macOS)
- Safari Mobile para iPad 2, iPad Mini, iPad con pantalla Retina (iOS 12 o posterior), para tienda de escritorio
- Safari Mobile para iPhone 6 o posterior; iOS 12 o posterior, para tienda móvil
- Chrome para móviles (versión principal más reciente y anterior) [Android 4 o posterior] para tienda móvil)

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) o posterior (solo entornos de desarrollo; puede tener un efecto adverso en el rendimiento)

>[!NOTE]
>
>Hay un problema conocido con `xdebug` que pueden afectar a las instalaciones de Adobe Commerce o de Magento Open Source o al acceso a la tienda o al administrador después de la instalación. Para obtener más información, consulte [Problema conocido con xdebug](https://support.magento.com/hc/en-us/articles/360034242212).
