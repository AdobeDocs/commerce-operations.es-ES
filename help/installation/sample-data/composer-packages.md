---
title: Descargar paquetes de Compositor de datos de ejemplo
description: Siga estos pasos para instalar datos de ejemplo de Adobe Commerce y Magento Open Source mediante el Administrador de paquetes PHP del compositor.
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Descargar paquetes de Compositor de datos de ejemplo

En esta sección se explica cómo instalar datos de ejemplo si tiene el software Adobe Commerce o de Magento Open Source de cualquiera de las siguientes maneras:

* Descarga de un archivo comprimido desde `https://magento.com/tech-resources/download`.

   Si ha descargado un archivo de GitHub, este método no funciona porque la variable `composer.json` el archivo no contiene el `repo.magento.com` URL.

* Utilizado `composer create-project`

Puede utilizar este método de obtención de datos de ejemplo tanto para Adobe Commerce como para Magento Open Source, pero debe utilizar el mismo [claves de autenticación](../prerequisites/authentication-keys.md) que utilizó para instalar la aplicación.

>[!NOTE]
>
>Si se producen errores, como `Could not find package...` o `...no matching package found...`, asegúrese de que no haya ningún error tipográfico en el comando. Si sigue encontrando errores, es posible que no tenga acceso a los repositorios de Composer adecuados, especialmente si está utilizando Adobe Commerce. Contacto [Asistencia de Adobe Commerce](https://support.magento.com/hc/en-us) para obtener ayuda.

Puede usar Composer para instalar datos de ejemplo antes o después de instalar la aplicación; sin embargo, es posible que [tareas adicionales](remove-or-update.md).

Si es un desarrollador colaborador, consulte [Instalación mediante clonación de repositorios](git-repositories.md).

>[!WARNING]
>
>No instale datos de ejemplo si la aplicación está configurada para [modo de producción](../../configuration/bootstrap/application-modes.md#production-mode). Cambiar a [modo de desarrollador](../../configuration/bootstrap/application-modes.md#developer-mode) primero. Instalación de datos de muestra en el modo de producción [falla](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Para instalar datos de ejemplo mediante la línea de comandos, introduzca el siguiente comando como propietario del sistema de archivos en la `<app_root>` directorio:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Si va a instalar datos de ejemplo _después_ Al instalar la aplicación, también debe ejecutar el siguiente comando para actualizar la base de datos y el esquema en la `<app_root>` directorio:

```bash
bin/magento setup:upgrade
```

Es necesario que [autentificar](../prerequisites/authentication-keys.md) para completar la acción.

## Error de autenticación

Puede aparecer el siguiente error de autenticación:

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Si aparece el error, cambie al directorio de instalación de la aplicación y ejecute `composer update`, que le solicita su [claves de autenticación](../prerequisites/authentication-keys.md).

## Completar la instalación de datos de ejemplo

{{$include /help/_includes/sample-data-complete.md}}
