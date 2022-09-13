---
title: Descargar paquetes del Compositor de datos de ejemplo
description: Siga estos pasos para instalar Adobe Commerce y los datos de ejemplo del Magento Open Source mediante el Administrador de paquetes PHP del Compositor.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---


# Descargar paquetes del Compositor de datos de ejemplo

En esta sección se explica cómo instalar datos de ejemplo si obtuvo el software Adobe Commerce o Magento Open Source de cualquiera de las siguientes maneras:

* Descarga de un archivo comprimido desde `https://magento.com/tech-resources/download`.

   Si ha descargado un archivo desde GitHub, este método no funciona porque la variable `composer.json` no contiene el `repo.magento.com` URL.

* Utilizado `composer create-project`

Puede utilizar este método para obtener datos de muestra tanto para Adobe Commerce como para Magento Open Source, pero debe utilizar el mismo [claves de autenticación](../prerequisites/authentication-keys.md) que utilizó para instalar la aplicación.

>[!NOTE]
>
>Si se producen errores, como `Could not find package...` o `...no matching package found...`, asegúrese de que no haya errores tipográficos en el comando. Si sigue encontrando errores, es posible que no tenga acceso a los repositorios del Compositor correctos, especialmente si utiliza Adobe Commerce. Contacto [Asistencia de Adobe Commerce](https://support.magento.com/hc/en-us) para obtener ayuda.

Puede utilizar Composer para instalar datos de ejemplo antes o después de instalar la aplicación; sin embargo, puede haber [tareas adicionales](remove-or-update.md).

Si es desarrollador colaborador, consulte [Instalación mediante la clonación de repositorios](git-repositories.md).

>[!WARNING]
>
>No instale datos de ejemplo si su aplicación está configurada para [modo de producción](../../configuration/bootstrap/application-modes.md#production-mode). Cambie a [modo de desarrollador](../../configuration/bootstrap/application-modes.md#developer-mode) primero. Instalación de datos de ejemplo en modo de producción [falla](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Para instalar datos de ejemplo utilizando la línea de comandos, introduzca el siguiente comando como propietario del sistema de archivos en la `<app_root>` directorio:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Si va a instalar datos de ejemplo _after_ al instalar la aplicación, también debe ejecutar el siguiente comando para actualizar la base de datos y el esquema en la `<app_root>` directorio:

```bash
bin/magento setup:upgrade
```

Debe [autenticar](../prerequisites/authentication-keys.md) para completar la acción.

## Error de autenticación

Puede aparecer el siguiente error de autenticación:

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Si aparece el error, cambie al directorio de instalación de la aplicación y ejecute `composer update`, que le pedirá que [claves de autenticación](../prerequisites/authentication-keys.md).

## Completar la instalación de datos de ejemplo

{{$include /help/_includes/sample-data-complete.md}}
