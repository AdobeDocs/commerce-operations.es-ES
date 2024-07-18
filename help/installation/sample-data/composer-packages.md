---
title: Descargar paquetes de Compositor de datos de ejemplo
description: Siga estos pasos para instalar datos de muestra de Adobe Commerce mediante el Compositor PHP Package Manager.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Descargar paquetes de Compositor de datos de ejemplo

En esta sección se explica cómo instalar datos de ejemplo si tiene el software de Adobe Commerce de cualquiera de las siguientes maneras:

* Descargó un archivo comprimido de `https://magento.com/tech-resources/download`.

  Si descargó un archivo de GitHub, este método no funciona porque el archivo `composer.json` no contiene la dirección URL `repo.magento.com`.

* Utilizó `composer create-project`

Puede utilizar este método para obtener datos de ejemplo para Adobe Commerce, pero debe utilizar las mismas [claves de autenticación](../prerequisites/authentication-keys.md) que utilizó para instalar la aplicación.

>[!NOTE]
>
>Si encuentra errores, como `Could not find package...` o `...no matching package found...`, asegúrese de que no haya errores tipográficos en el comando. Si sigue encontrando errores, es posible que no tenga acceso a los repositorios de Composer adecuados, especialmente si está utilizando Adobe Commerce. Póngase en contacto con el [Soporte técnico de Adobe Commerce](https://support.magento.com/hc/en-us) para obtener ayuda.

Puede usar Composer para instalar datos de ejemplo antes o después de instalar la aplicación; sin embargo, puede haber [tareas adicionales](remove-or-update.md).

Si usted es un desarrollador colaborador, consulte [Instalar clonando repositorios](git-repositories.md).

>[!WARNING]
>
>No instale datos de ejemplo si su aplicación está configurada para [modo de producción](../../configuration/bootstrap/application-modes.md#production-mode). Cambie primero a [modo de desarrollador](../../configuration/bootstrap/application-modes.md#developer-mode). La instalación de datos de ejemplo en el modo de producción [falla](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Para instalar datos de ejemplo mediante la línea de comandos, escriba el comando siguiente como propietario del sistema de archivos en el directorio `<app_root>`:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Si va a instalar los datos de ejemplo _después de_ de instalar la aplicación, también debe ejecutar el siguiente comando para actualizar la base de datos y el esquema en el directorio `<app_root>`:

```bash
bin/magento setup:upgrade
```

Se le requiere que [se autentique](../prerequisites/authentication-keys.md) para completar la acción.

## Error de autenticación

Puede aparecer el siguiente error de autenticación:

```
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Si aparece el error, cambie al directorio de instalación de la aplicación y ejecute `composer update`, que le pedirá las [claves de autenticación](../prerequisites/authentication-keys.md).

## Completar la instalación de datos de ejemplo

{{$include /help/_includes/sample-data-complete.md}}
