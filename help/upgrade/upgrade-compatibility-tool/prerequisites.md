---
title: "[!DNL Upgrade Compatibility Tool] requisitos"
description: Verifique que su sistema cumpla los requisitos necesarios para ejecutar el [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos para su proyecto de Adobe Commerce.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---


# Claves de acceso de Adobe Commerce

{{commerce-only}}

Debe tener [Claves de acceso de Adobe Commerce](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) para descargar y usar el [!DNL Upgrade Compatibility Tool]. Añada sus claves de acceso de Adobe Commerce a su `auth.json` que se encuentra en `~/.composer` de forma predeterminada.

>[!NOTE]
>
>Compruebe su **COMPOSER_HOME** variable de entorno para ver dónde está la variable `auth.json` se encuentra.

La variable **clave pública** corresponde a la variable _username_ que **clave privada** es la variable _password_:

## Ejemplo de claves de acceso de Adobe Commerce

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

>[!NOTE]
>
> Si no configura correctamente su **Claves de acceso de Adobe Commerce**, no puede descargar el [!DNL Upgrade Compatibility Tool] y `composer create-project` fallará.

Ejecutar `composer install` en su terminal para instalar dependencias.

## Requisitos del sistema

Los requisitos mínimos para utilizar la variable [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos:

| **Requisitos** | **Restricciones** |
|----------------|-----------------|
| Versión de PHP | >= 7.3 |
| Compositor | no se conoce ningún requisito. |
| Node.js | Versiones de Node.js `^12.22.0`, `^14.17.0`o `>=16.0.0` (consulte [Instalar Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs/)) |
| Limitaciones de memoria | Al menos 2 GB de RAM. |

[!DNL Upgrade Compatibility Tool] requirements [PCNTL](https://www.php.net/manual/en/book.pcntl.php) y otras extensiones PHP para la ejecución. Compruebe las extensiones PHP requeridas utilizando `composer check-platform-reqs` comando:

```bash
# Example output of `composer check-platform-reqs` command for UCT 2.2.6 and PHP 7.4:

$ composer check-platform-reqs
Checking platform requirements for packages in the vendor dir
ext-ctype     *         success provided by symfony/polyfill-ctype
ext-dom       20031129  success
ext-filter    7.4.30    success
ext-json      7.4.30    success
ext-libxml    7.4.30    success
ext-mbstring  *         success provided by symfony/polyfill-mbstring
ext-openssl   7.4.30    success
ext-pcntl     7.4.30    success
ext-pcre      7.4.30    success
ext-phar      7.4.30    success
ext-simplexml 7.4.30    success
ext-tokenizer 7.4.30    success
ext-xml       7.4.30    success
ext-xmlwriter 7.4.30    success
ext-zip       1.15.6    success
php           7.4.30    success
```

Adobe Commerce solo es compatible con sistemas operativos Linux. Puede ejecutar el [!DNL Upgrade Compatibility Tool] en un sistema operativo Linux. No es necesario ejecutar el [!DNL Upgrade Compatibility Tool] donde se encuentra la instancia de Adobe Commerce.

Es necesario para el [!DNL Upgrade Compatibility Tool] para tener acceso al código fuente de la instancia de Adobe Commerce. Por ejemplo, puede instalarlo en un servidor y señalarlo en la instalación de Adobe Commerce en otro servidor.

Si está ejecutando el [!DNL Upgrade Compatibility Tool] en una instancia de Adobe Commerce con módulos y archivos grandes, la herramienta podría requerir una gran cantidad de RAM (al menos 2 GB).
