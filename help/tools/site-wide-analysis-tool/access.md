---
title: Cómo acceder a [!DNL Site-Wide Analysis Tool]
description: Obtenga información sobre cómo acceder a [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Cómo acceder a [!DNL Site-Wide Analysis Tool]

El [!DNL Site-Wide Analysis Tool] El servicio está disponible en [modo de producción](https://docs.magento.com/user-guide/magento/installation-modes.html) para [!DNL Admin] usuarios con permiso para acceder a usuario [recursos de rol](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>Si tiene una instalación local de Adobe Commerce, debe instalar un [agente](../site-wide-analysis-tool/installation.md) en su infraestructura para utilizar la herramienta.

![Tablero de análisis de todo el sitio](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Tablero*

## Paso 1: Verificar los permisos

Compruebe que la variable [!DNL Admin] La cuenta de usuario de tiene permiso para acceder a [!DNL Site-Wide Analysis Tool] a través de su [función de usuario asignada](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>El [!DNL Site-Wide Analysis Tool] el recurso de rol (permiso) es **no** asignado automáticamente. DEBE activarse para la función de usuario y la función asignada individualmente a cada cuenta de usuario en la [!UICONTROL Admin].

Para la función personalizada que necesita [!DNL Site-Wide Analysis Tool] para acceder a, haga lo siguiente:

1. Seleccione el **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** recurso de rol.

   ![Tablero de análisis de todo el sitio](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]permiso seleccionado para el rol*

1. Clic **[!UICONTROL Save Role]**.

1. Notificar a los usuarios que tengan asignada esa función para que cierren sesión en [!DNL Admin]y vuelva a iniciar sesión.

>[!NOTE]
>
>Si ha comprobado que la cuenta de usuario tiene permiso para acceder a [!DNL Site-Wide Analysis Tool] y el usuario recibe un error 403 al intentar acceder a la herramienta desde el [!DNL Admin]Sin embargo, su instancia de Adobe Commerce en la infraestructura de la nube podría tener habilitado el control de acceso HTTP. El [!DNL Site-Wide Analysis Tool] El panel NO es compatible si tiene habilitada la autenticación HTTP. Para obtener más información sobre cómo resolver este problema, consulte nuestra [Artículo de soporte](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

## Paso 2: Acceso [!DNL Site-Wide Analysis Tool]

1. En el *[!UICONTROL Admin]* barra lateral, vaya a **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

1. Lea el *Condiciones de uso* para el [!DNL Site-Wide Analysis Tool] y haga clic en **[!UICONTROL Accept]** para continuar.

   Cada usuario debe aceptar las Condiciones de uso de la sesión. Este paso se repite en cada sesión iniciada.

   ![Tablero de análisis de todo el sitio](../../assets/tools/swat-tos.png)
   *Condiciones de uso*

1. En la parte superior del panel, haga clic en la pestaña que desee ver.

   ![Tablero de análisis de todo el sitio](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]información*

## Paso 3: Generación del informe

1. En la esquina superior derecha del panel, haga clic en **[!UICONTROL Generate Report]**.

1. Seleccione la casilla de verificación de cada **[!UICONTROL Type]** y **[!UICONTROL Priority]** configuración que desea incluir en el informe.

1. Clic **[!UICONTROL Generate Report]**.

   ![Tablero de análisis de todo el sitio](../../assets/tools/swat-report-settings.png)
   *Configuración de informes*

| TABULACIÓN | DESCRIPCIÓN |
| --- | --- |
| Tablero | Muestra el estado del sistema con las notificaciones y recomendaciones actuales por prioridad. |
| Información | Proporciona información de contacto del cliente y un resumen de los tickets actuales, con información detallada sobre cada producto de Adobe Commerce instalado. |
| Recommendations | Enumera recomendaciones basadas en prácticas recomendadas para abordar los problemas detectados en el sitio. |
| Excepciones | Enumera los errores producidos por la aplicación debido a condiciones anómalas sin un controlador de errores. |
| Extensiones | Enumera todas las extensiones de terceros y bibliotecas de terceros. |

>[!NOTE]
>
>Después de aplicar una recomendación, puede tardar unos días en actualizarse en el [!DNL Site-Wide Analysis Tool] Panel o informe generado.
