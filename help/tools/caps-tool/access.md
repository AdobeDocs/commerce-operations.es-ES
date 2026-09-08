---
title: Cómo tener acceso a  [!DNL Adobe Commerce Patching Automation]
description: Obtenga información sobre cómo acceder y utilizar  [!DNL Adobe Commerce Patching Automation]
source-git-commit: d9f6fc714332638ae1dcfa92ac8abe274efe8a0b
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 1%

---

# Cómo acceder a [!DNL Adobe Commerce Patching Automation]

## Requisitos previos

[!DNL Patching Automation] utiliza el control de acceso basado en roles de Adobe Commerce Cloud. El nivel de acceso en Cloud Console determina lo que puede hacer con el servicio.

### Quién puede usar [!DNL Patching Automation]

* **Administrador de proyecto**: puede aplicar o revertir parches en todos los entornos
* **Colaborador**: puede aplicar o revertir parches en los entornos asignados
* **Visor**: solo se puede ver el proyecto y los entornos, no se permiten acciones

### Solicitud de acceso a un proyecto

Si no ve ningún proyecto en la interfaz de usuario de [!DNL Patching Automation], solicite acceso a la persona apropiada:

* Póngase en contacto con el propietario de la cuenta o el administrador del proyecto
* Ellos le otorgarán la función adecuada a través de la consola de Cloud
* Una vez concedido el acceso, puede iniciar sesión en Cloud Console para utilizar el servicio

>[!NOTE]
>
>[!DNL Patching Automation] sigue el mismo modelo de permisos que Adobe Commerce Cloud, por lo que su nivel de acceso en Cloud Console determina lo que puede hacer con el servicio.

## Acceder a [!DNL Patching Automation]

[!DNL Patching Automation] está disponible como una ficha dentro del panel [!DNL Site-Wide Analysis Tool]. Puede acceder a él desde el Panel de administración desde **Informes** > **Información del sistema** > **Herramienta de análisis de todo el sitio** en la barra lateral de administración. Consulte [Cómo acceder a la herramienta de análisis de todo el sitio](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/site-wide-analysis-tool/access) para conocer los requisitos previos y la configuración de permisos.

Una vez que esté en el panel:

1. Haga clic en la ficha [!UICONTROL Patching Automation] de la interfaz.
1. Seleccione el proyecto y el entorno en el que desea aplicar los parches.
1. Revise los parches disponibles y su estado de compatibilidad.
1. Seleccione parches para aplicar o revertir.

## Acceso al entorno de producción

Para entornos de producción, se aplican garantías adicionales de forma predeterminada:

* **Modo de mantenimiento** - Debe estar habilitado
* **Trabajos cron** - Deben deshabilitarse
* **Cuadro de diálogo de confirmación** - Debe completarse antes de continuar

>[!IMPORTANT]
>
>La aplicación de parches en el entorno de producción requiere una preparación adecuada y medidas de seguridad para evitar interrupciones accidentales.

>[!NOTE]
>
>Puede omitir las comprobaciones del modo de mantenimiento y del trabajo cron seleccionando la casilla de verificación de anulación en la interfaz de usuario (*[!UICONTROL I want to skip maintenance mode and cron checks before applying patches to production environment]*). Utilice esto solo si comprende el riesgo de aplicar parches a la producción sin estas garantías.

## Temas relacionados

* [Introducción a la automatización de parches](intro.md)
* [Resumen de flujo de trabajo](workflow.md)
* [Integración de GitHub](github-integration.md)
* [Prácticas recomendadas](best-practices.md)
* [Resolución de problemas](troubleshooting.md)
