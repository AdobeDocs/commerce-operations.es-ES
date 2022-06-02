---
title: '"[!DNL Upgrade Compatibility Tool] requisitos"'
description: 'Verifique que su sistema cumpla los requisitos necesarios para ejecutar el [!DNL Upgrade Compatibility Tool] para su proyecto de Adobe Commerce. '
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---


# Requisitos del sistema

{{commerce-only}}

Los requisitos mínimos para utilizar la variable [!DNL Upgrade Compatibility Tool] son:

| **Requisitos** | **Restricciones** |
|----------------|-----------------|
| Versión de PHP | >= 7,3 |
| Compositor | ningún requisito conocido |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`o `>=16.0.0`) |
| Limitaciones de memoria | Al menos 2 GB de RAM |

Puede ejecutar el [!DNL Upgrade Compatibility Tool] en varios sistemas operativos (Windows no es compatible). No es necesario ejecutar el [!DNL Upgrade Compatibility Tool] donde se encuentra la instancia de Adobe Commerce.

Es necesario para el [!DNL Upgrade Compatibility Tool] para tener acceso al código fuente de la instancia de Adobe Commerce. Por ejemplo, puede instalarlo en un servidor y señalarlo en la instalación de Adobe Commerce en otro servidor.

Si está ejecutando el [!DNL Upgrade Compatibility Tool] en una instancia de Adobe Commerce con módulos y archivos grandes, la herramienta podría requerir una gran cantidad de RAM (al menos 2 GB).

## Claves de acceso de Adobe Commerce

Debe tener [Claves de acceso de Adobe Commerce](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) para descargar y usar el [!DNL Upgrade Compatibility Tool]. Añada sus claves de acceso de Adobe Commerce a su `auth.json` que se encuentra en `~/.composer` de forma predeterminada.

>[!WARNING]
>
>Compruebe su **COMPOSER_HOME** variable de entorno para ver dónde está la variable `auth.json` se encuentra.

La variable **clave pública** corresponde a la variable _username_ que **clave privada** es la variable _password_:

### Ejemplo de claves de acceso de Adobe Commerce

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

## Compositor

Descargue el [!DNL Upgrade Compatibility Tool] repositorio y ejecutar `composer install` en su terminal para instalar dependencias.

>[!NOTE]
>
> Si no configura correctamente su **Claves de acceso de Adobe Commerce**, no puede descargar el [!DNL Upgrade Compatibility Tool]. Ejecución de `composer create-project` fallará.

## Node.js

Para instalar Node.js, consulte Node.js [documentación](https://nodejs.dev/learn/how-to-install-nodejs).

## Extensiones de terceros

Adobe recomienda ponerse en contacto con el proveedor de extensiones para determinar si la extensión es totalmente compatible con la última versión de Adobe Commerce.
