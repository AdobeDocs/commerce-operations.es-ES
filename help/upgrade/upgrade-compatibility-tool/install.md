---
title: Descargue el [!DNL Upgrade Compatibility Tool]
description: Siga estos pasos para descargar el [!DNL Upgrade Compatibility Tool] para su proyecto de Adobe Commerce.
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---


# Instale el [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

La variable [!DNL Upgrade Compatibility Tool] es una herramienta de línea de comandos que comprueba una instancia personalizada de Adobe Commerce en una versión específica analizando todos los módulos instalados en ella. Devuelve una lista de errores y advertencias que deben solucionarse antes de actualizar a la última versión de Adobe Commerce.

## Requisitos previos

Para instalar el [!DNL Upgrade Compatibility Tool], debe instalar los requisitos previos necesarios.

Consulte [requisitos previos](../upgrade-compatibility-tool/prerequisites.md) para obtener más información.

## Descargue el [!DNL Upgrade Compatibility Tool]

Para descargar el [!DNL Upgrade Compatibility Tool], ejecute el siguiente comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Claves de acceso de Adobe Commerce

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

### Compositor

Descargue el [!DNL Upgrade Compatibility Tool] repositorio y ejecutar `composer install` en su terminal para instalar dependencias.

>[!WARNING]
>
>Si la variable **Claves de acceso de Adobe Commerce** no están correctamente configurados, no puede descargar la [!DNL Upgrade Compatibility Tool] y al ejecutar el `composer create-project` fallará.

### Node.js

Para instalar Node.js, consulte Node.js [documentación](https://nodejs.dev/learn/how-to-install-nodejs).

## Extensiones de terceros

Adobe recomienda ponerse en contacto con el proveedor de extensiones para determinar si la extensión es totalmente compatible con la última versión de Adobe Commerce.

Consulte [Ejecutar la herramienta](../upgrade-compatibility-tool/run.md) para obtener información sobre cómo ejecutar el [!DNL Upgrade Compatibility Tool].
