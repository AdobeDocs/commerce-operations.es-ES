---
title: '[!DNL Upgrade Compatibility Tool] requisitos'
description: Compruebe que el sistema cumple los requisitos necesarios para ejecutar el [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos para el proyecto de Adobe Commerce.
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Claves de acceso de Adobe Commerce

{{commerce-only}}

Debe tener [Claves de acceso de Adobe Commerce](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) para descargar y utilizar [!DNL Upgrade Compatibility Tool]. Añada sus claves de acceso de Adobe Commerce a su `auth.json` , que se encuentra en `~/.composer` de forma predeterminada.

>[!NOTE]
>
>Compruebe su **COMPOSER_HOME** variable de entorno para ver dónde está el `auth.json` se encuentra el archivo.

El **clave pública** corresponde al _nombre de usuario_ Considerando que la **clave privada** es el _contraseña_:

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
> Si no configura correctamente la variable **Claves de acceso de Adobe Commerce**, no puede descargar el [!DNL Upgrade Compatibility Tool] y el `composer create-project` El comando fallará.

Ejecutar `composer install` en el terminal para instalar dependencias.

## Requisitos del sistema

Requisitos mínimos para utilizar el [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos:

| **Requisitos** | **Restricciones** |
|----------------|-----------------|
| Versión de PHP | >= 7.3 |
| Compositor | no se conoce ningún requisito. |
| Node.js | Versiones de Node.js `^12.22.0`, `^14.17.0`, o `>=16.0.0` (consulte [Instalar Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs/)) |
| Limitaciones de memoria | Al menos 2 GB de RAM. |

[!DNL Upgrade Compatibility Tool] requiere [PCNTL](https://www.php.net/manual/en/book.pcntl.php) y otras extensiones PHP para la ejecución. Compruebe las extensiones PHP necesarias utilizando `composer check-platform-reqs` comando:

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

Adobe Commerce solo es compatible con sistemas operativos Linux. Puede ejecutar el [!DNL Upgrade Compatibility Tool] en un sistema operativo Linux. No tiene que ejecutar el [!DNL Upgrade Compatibility Tool] donde se encuentra su instancia de Adobe Commerce.

Es necesario para el [!DNL Upgrade Compatibility Tool] para tener acceso al código fuente de la instancia de Adobe Commerce. Por ejemplo, puede instalarlo en un servidor y dirigirlo a la instalación de Adobe Commerce en otro servidor.

Si está ejecutando el [!DNL Upgrade Compatibility Tool] en una instancia de Adobe Commerce con módulos y archivos grandes, la herramienta puede requerir una gran cantidad de RAM (al menos 2 GB).

Ejecute el [!DNL Upgrade Compatibility Tool] desde el [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) para [Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} proyectos.
