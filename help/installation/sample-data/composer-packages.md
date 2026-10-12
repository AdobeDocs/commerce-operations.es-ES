---
title: Descargar paquetes de Compositor de datos de ejemplo
description: Siga estos pasos para instalar datos de muestra de Adobe Commerce mediante el Compositor PHP Package Manager.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
last-update: 2026-04-28
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a3c0eba7bdcd8017e88bdb4df1f45d77fe4bb351
workflow-type: tm+mt
source-wordcount: '302'
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

```shell
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Si va a instalar los datos de ejemplo _después de_ de instalar la aplicación, también debe ejecutar el siguiente comando para actualizar la base de datos y el esquema en el directorio `<app_root>`:

```shell
bin/magento setup:upgrade
```

Se le requiere que [se autentique](../prerequisites/authentication-keys.md) para completar la acción.

## Error de autenticación

Puede aparecer el siguiente error de autenticación:

```text
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Si aparece el error, cambie al directorio de instalación de la aplicación y ejecute `composer update`, que le pedirá las [claves de autenticación](../prerequisites/authentication-keys.md).

## Completar la instalación de datos de ejemplo

{{$include /help/_includes/sample-data-complete.md}}

<!-- Last updated from includes: 2026-04-17 13:49:36 -->
