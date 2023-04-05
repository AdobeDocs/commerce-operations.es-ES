---
title: Requisitos del sistema
description: Utilice esta referencia para identificar las dependencias de software necesarias que se han probado con las versiones de Adobe Commerce y Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# Requisitos del sistema

Esta tabla muestra versiones de dependencias de software de terceros que el Adobe ha probado con versiones específicas de Adobe Commerce y Magento Open Source. Adobe solo admite la combinación de requisitos del sistema que se describe en la siguiente tabla.

Por ejemplo, 2.4.5 se ha probado completamente con MariaDB 10.4. Adobe recomienda actualizar a MariaDB 10.4 antes de actualizar a 2.4.5.

{{$include /help/_includes/templated/system-requirements-table.md}}

## Varios

En esta sección se describe la compatibilidad y compatibilidad con todos los demás tipos de software opcionales y requeridos.

>[!NOTE]
>
>Los siguientes requisitos se aplican a la última versión de parches 2.4.x de Adobe Commerce y Magento Open Source.

### Servidor de correo

Agente de transferencia de correo (MTA) o un servidor SMTP

### Sistemas operativos (Linux x86-64)

Distribuciones Linux, como RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian, y similares. Microsoft Windows y macOS no son compatibles.

### Extensiones PHP

>[!NOTE]
>
>La variable [Instrucciones de instalación de PHP](prerequisites/php-settings.md) incluya un paso para instalar estas extensiones.

{{$include /help/_includes/templated/php-extensions.md}}

Consulte [documentación oficial de PHP](https://php.net/manual/en/extensions.php) para obtener más información sobre la instalación.

### PHP OPcache

Le recomendamos encarecidamente que verifique que [PHP OPcache](https://php.net/manual/en/intro.opcache.php) está habilitado por motivos de rendimiento. El OPcache está habilitado en muchas distribuciones PHP. Para comprobar si está instalado, consulte nuestra [Documentación de PHP](prerequisites/php-settings.md).

Si debe instalarlo por separado, consulte la [Documentación de PHP OPcache](https://php.net/manual/en/opcache.setup.php).

### Configuración de PHP

Recomendamos configuraciones de PHP particulares, como `memory_limit`, que pueden evitar problemas comunes al utilizar Adobe Commerce y Magento Open Source.

Para obtener más información, consulte [Configuración de PHP requerida](prerequisites/php-settings.md).

### PHPUnit

PHPUnit (como herramienta de línea de comandos) 9.0.0

### RAM

La actualización de las aplicaciones y extensiones que obtiene del Commerce Marketplace y otras fuentes puede requerir hasta 2 GB de RAM. Si está utilizando un sistema con menos de 2 GB de RAM, le recomendamos que cree un [intercambiar archivo](https://support.magento.com/hc/en-us/articles/360032980432); de lo contrario, es posible que la actualización falle.

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
- No se admiten certificados SSL autofirmados.
- Requisito de Seguridad de capa de transporte (TLS): PayPal y `repo.magento.com` ambos requieren TLS 1.2 o posterior.

### Navegadores admitidos

Tienda y administrador:

- Microsoft Edge (última y anterior versión principal)
- Firefox (versión principal más reciente y anterior; cualquier sistema operativo)
- Chrome (última y anterior versión principal; cualquier sistema operativo)
- Safari (versión principal más reciente y anterior); Solo macOS)
- Safari Mobile para iPad 2, iPad Mini, iPad con pantalla Retina (iOS 12 o posterior) para tienda de escritorio
- Safari Mobile para iPhone 6 o posterior; iOS 12 o posterior, para tienda móvil
- Chrome para dispositivos móviles (versión más reciente y anterior) [Android 4 o posterior] para tienda móvil)

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) o posterior (solo entornos de desarrollo; puede tener un efecto adverso sobre el rendimiento)

>[!NOTE]
>
>Hay un problema conocido con `xdebug` que pueden afectar a las instalaciones de Adobe Commerce o Magento Open Source, o al acceso a la tienda o al administrador después de la instalación. Para obtener más información, consulte [Problema conocido con xdebug](https://support.magento.com/hc/en-us/articles/360034242212).
