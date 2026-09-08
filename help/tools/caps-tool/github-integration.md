---
title: Configurar la integración de GitHub para  [!DNL Adobe Commerce Patching Automation]
description: Aprenda a instalar la aplicación  [!DNL Adobe Commerce Patching Automation] GitHub para habilitar las operaciones de revisión en los proyectos de Adobe Commerce Cloud conectados a GitHub.
source-git-commit: d9f6fc714332638ae1dcfa92ac8abe274efe8a0b
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---


# Configurar la integración de GitHub para [!DNL Patching Automation]

Si su proyecto de Adobe Commerce Cloud está conectado a un repositorio de GitHub, debe instalar la aplicación GitHub [!DNL Patching Automation] para poder utilizar el servicio para aplicar o revertir parches. La aplicación concede al servicio el acceso que necesita para realizar cambios en el repositorio en su nombre.

## Requisitos previos

* Una suscripción activa a Adobe Commerce Cloud
* Ya hay configurada una [integración de GitHub](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github) para su proyecto de Adobe Commerce Cloud, con su opción [`fetch-branches` habilitada](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration). [!DNL Patching Automation] crea y inserta ramas de entorno de integración temporales, por lo que las operaciones de revisión no pueden crear el entorno cuando esta opción está deshabilitada.
* Repositorio alojado en [!DNL github.com]. No se admiten integraciones de GitHub configuradas con un dominio personalizado.
* Acceso de propietario o administrador a la organización o al repositorio de GitHub

## Instalar la aplicación GitHub [!DNL Patching Automation]

Puede iniciar la instalación desde [!DNL Patching Automation] si hace clic en **[!UICONTROL Install GitHub App]** en la interfaz de usuario, que le redirigirá a la página de instalación, o si navega directamente a la página de instalación.

1. Abra la [página de instalación de la aplicación GitHub de automatización de parches](https://github.com/apps/adobe-commerce-patching-automation).
1. Haga clic en **[!UICONTROL Install]**.
1. Seleccione la organización de GitHub que posee el repositorio de Adobe Commerce.
1. En **[!UICONTROL Repository access]**, seleccione **[!UICONTROL Only select repositories]** y elija el repositorio para su proyecto de Adobe Commerce.
1. Haga clic en **[!UICONTROL Install]** para confirmar.

Una vez instalado, el servicio detecta automáticamente la conexión de GitHub y utiliza la aplicación para todas las operaciones de parche. No se requiere ninguna otra configuración.

## Comprobación y administración del estado de la conexión

La interfaz de usuario [!DNL Patching Automation] muestra el estado actual de su conexión a GitHub, con acciones disponibles según ese estado:

* **[!UICONTROL Refresh]** / **[!UICONTROL Refresh status]** - Vuelve a comprobar el estado de la conexión sin realizar ningún cambio.
* **[!UICONTROL Reinstall]**: se muestra si la instalación ya no es válida (por ejemplo, si se suspendió o si se cambió el repositorio conectado a su proyecto de Cloud). Inicia el mismo flujo de instalación descrito anteriormente.
* **[!UICONTROL Unlink GitHub App]** - Elimina la conexión guardada de [!DNL Patching Automation] a la aplicación de GitHub. Esto hace que **no** desinstale la aplicación de su repositorio de GitHub; para eliminar completamente el acceso, consulte la sección Desinstalar a continuación.

## Desinstalar la aplicación GitHub [!DNL Patching Automation]

Si ya no desea que el servicio acceda al repositorio:

1. En GitHub, abra la configuración de la cuenta propietaria de la instalación:
   * Para un repositorio de **propiedad de la organización**: **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**.
   * Para un repositorio **personal**: **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**.
1. Busque `adobe-commerce-patching-automation` y haga clic en **[!UICONTROL Configure]**.
1. Haga clic en **[!UICONTROL Uninstall]** y confirme.

>[!WARNING]
>
>Si alguna operación de aplicación o reversión sigue en curso cuando se desinstala la aplicación de GitHub, es posible que esas operaciones fallen. Después de desinstalar la aplicación, los usuarios no pueden iniciar nuevas operaciones porque los botones de acción quedan inactivos.

## Temas relacionados

* [Introducción a la automatización de parches](intro.md)
* [Cómo acceder a](access.md)
* [Resumen de flujo de trabajo](workflow.md)
* [Prácticas recomendadas](best-practices.md)
* [Resolución de problemas](troubleshooting.md)
