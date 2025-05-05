---
title: '[!DNL Upgrade Compatibility Tool] requisitos'
description: Compruebe que el sistema cumple los requisitos necesarios para ejecutar  [!DNL Upgrade Compatibility Tool]  en una interfaz de línea de comandos para el proyecto de Adobe Commerce.
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# Claves de acceso de Adobe Commerce

{{commerce-only}}

Debe tener [claves de acceso de Adobe Commerce](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) para descargar y usar [!DNL Upgrade Compatibility Tool]. Agregue sus claves de acceso de Adobe Commerce al archivo `auth.json`, que se encuentra en `~/.composer` de forma predeterminada.

>[!NOTE]
>
>Compruebe su variable de entorno **COMPOSER_HOME** para ver dónde se encuentra el archivo `auth.json`.

La **clave pública** corresponde al _nombre de usuario_, mientras que la **clave privada** es la _contraseña_:

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
> Si no configura correctamente sus **claves de acceso de Adobe Commerce**, no podrá descargar [!DNL Upgrade Compatibility Tool] y el comando `composer create-project` fallará.

Ejecute `composer install` en el terminal para instalar dependencias.

## Requisitos del sistema

Los requisitos mínimos para usar [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos son:

| **Requisitos** | **Restricciones** |
|----------------|-----------------|
| Versión de PHP | >= 7,3 |
| Compositor | no se conoce ningún requisito. |
| Node.js | Versiones de Node.js `^12.22.0`, `^14.17.0` o `>=16.0.0` (consulte [Instalar Node.js](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)) |
| Limitaciones de memoria | Al menos 2 GB de RAM. |

[!DNL Upgrade Compatibility Tool] requiere [PCNTL](https://www.php.net/manual/en/book.pcntl.php) y otras extensiones PHP para la ejecución. Compruebe las extensiones PHP necesarias con el comando `composer check-platform-reqs`:

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

Adobe Commerce solo es compatible con sistemas operativos Linux. Puede ejecutar [!DNL Upgrade Compatibility Tool] en un sistema operativo Linux. No tiene que ejecutar [!DNL Upgrade Compatibility Tool] donde se encuentra la instancia de Adobe Commerce.

Es necesario que [!DNL Upgrade Compatibility Tool] tenga acceso al código fuente de la instancia de Adobe Commerce. Por ejemplo, puede instalarlo en un servidor y dirigirlo a la instalación de Adobe Commerce en otro servidor.

Si está ejecutando [!DNL Upgrade Compatibility Tool] en una instancia de Adobe Commerce con módulos y archivos grandes, es posible que la herramienta requiera una gran cantidad de RAM (al menos 2 GB).

Ejecutar [!DNL Upgrade Compatibility Tool] desde [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html?lang=es) para [Adobe Commerce en proyectos de infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=es){target=_blank}.
