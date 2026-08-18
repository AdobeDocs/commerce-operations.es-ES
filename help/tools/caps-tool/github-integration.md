---
title: Configurar la integración de GitHub para  [!DNL CAPS]
description: Aprenda a instalar la aplicación  [!DNL Cloud Automation Patching Service (CAPS)] GitHub para habilitar las operaciones de revisión en los proyectos de Adobe Commerce Cloud conectados a GitHub.
hide: true
source-git-commit: 2887956e8644ffbcaadde36b90a0fc984369008a
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 1%

---


# Configurar la integración de GitHub para [!DNL CAPS]

Si el proyecto de Adobe Commerce Cloud está conectado a un repositorio de GitHub, debe instalar la aplicación GitHub [!DNL CAPS] para poder usar [!DNL Cloud Automation Patching Service] ([!DNL CAPS]) para aplicar o revertir parches. La aplicación concede a [!DNL CAPS] el acceso que necesita para realizar cambios en el repositorio en su nombre.

## Requisitos previos

* Una suscripción activa a Adobe Commerce Cloud
* Ya hay configurada una [integración de GitHub](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github) para su proyecto de Adobe Commerce Cloud, con su opción [`fetch-branches` habilitada](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration). [!DNL CAPS] crea y inserta ramas de entorno de integración temporales, por lo que las operaciones de revisión no pueden crear el entorno cuando esta opción está deshabilitada.
* Repositorio alojado en [!DNL github.com]. No se admiten integraciones de GitHub configuradas con un dominio personalizado.
* Acceso de propietario o administrador a la organización o al repositorio de GitHub

## Instalar la aplicación GitHub [!DNL CAPS]

1. Abra la [página de instalación de la aplicación GitHub de CAPS](https://github.com/apps/adobe-commerce-patching-automation).
1. Haga clic en **[!UICONTROL Install]**.
1. Seleccione la organización de GitHub que posee el repositorio de Adobe Commerce.
1. En **[!UICONTROL Repository access]**, seleccione **[!UICONTROL Only select repositories]** y elija el repositorio para su proyecto de Adobe Commerce.
1. Haga clic en **[!UICONTROL Install]** para confirmar.

Una vez instalado, [!DNL CAPS] detecta automáticamente su conexión de GitHub y utiliza la aplicación para todas las operaciones de parche. No se requiere ninguna otra configuración.

## Desinstalar la aplicación GitHub [!DNL CAPS]

Si ya no desea que [!DNL CAPS] acceda al repositorio:

1. En GitHub, abra la configuración de la cuenta propietaria de la instalación:
   * Para un repositorio de **propiedad de la organización**: **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**.
   * Para un repositorio **personal**: **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**.
1. Busque `adobe-commerce-patching-automation` y haga clic en **[!UICONTROL Configure]**.
1. Haga clic en **[!UICONTROL Uninstall]** y confirme.

>[!WARNING]
>
>Si hay operaciones de aplicación o reversión de CAPS en curso cuando se desinstala la aplicación GitHub, es posible que dichas operaciones fallen. Después de desinstalar la aplicación, los usuarios no pueden iniciar nuevas operaciones porque los botones de acción quedan inactivos.

## Temas relacionados

* [Introducción a CAPS](intro.md)
* [Cómo acceder a](access.md)
* [Resumen de flujo de trabajo](workflow.md)
* [Prácticas recomendadas](best-practices.md)
* [Resolución de problemas](troubleshooting.md)
