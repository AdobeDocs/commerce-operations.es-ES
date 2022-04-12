---
title: Acceso [!DNL Site-Wide Analysis Tool]
description: Obtenga información sobre cómo acceder al [!DNL Site-Wide Analysis Tool]
source-git-commit: c7fabdd83e03a288d627b70d48cdf57184d43603
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Cómo acceder a la variable [!DNL Site-Wide Analysis Tool]

La variable [!DNL Site-Wide Analysis Tool] está disponible en [modo de producción](https://docs.magento.com/user-guide/magento/installation-modes.html) para [!DNL Admin] usuarios con permiso para acceder al usuario [recursos de rol](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>Si tiene una instalación local de Adobe Commerce, debe instalar un [agente](../site-wide-analysis-tool/installation.md) en su infraestructura para utilizar la herramienta.

![Tablero de análisis de todo el sitio](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Panel*

## Paso 1: Comprobar permisos

Compruebe que la variable [!DNL Admin] la cuenta de usuario tiene permiso para acceder al [!DNL Site-Wide Analysis Tool] a través de sus [rol de usuario asignado](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>La variable [!DNL Site-Wide Analysis Tool] recurso de rol (permiso) es **not** asignación automática. DEBE activarse para la función de usuario y la función asignada individualmente a cada cuenta de usuario en la variable [!UICONTROL Admin].

Para la función personalizada que necesita [!DNL Site-Wide Analysis Tool] haga lo siguiente:

1. Seleccione el **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** recurso de rol.

   ![Tablero de análisis de todo el sitio](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]permiso seleccionado para la función*

1. Haga clic **[!UICONTROL Save Role]**.

1. Notificar a los usuarios a los que se les asigne esa función que cierren la sesión de [!DNL Admin]e inicie sesión de nuevo.

>[!NOTE]
>
>Si ha verificado que la cuenta de usuario tiene permiso para acceder a la variable [!DNL Site-Wide Analysis Tool] y el usuario recibe un error 403 al intentar acceder a la herramienta desde la variable [!DNL Admin], la instancia de Adobe Commerce en la infraestructura de nube podría tener habilitado el control de acceso HTTP. La variable [!DNL Site-Wide Analysis Tool] Dashboard NO es compatible si tiene habilitada la autenticación HTTP. Para obtener más información sobre la resolución de este problema, consulte nuestra [Artículo de asistencia](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

## Paso 2: Acceso [!DNL Site-Wide Analysis Tool]

1. En el *[!UICONTROL Admin]* barra lateral, vaya a **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

1. Lea el *Condiciones de uso* para el [!DNL Site-Wide Analysis Tool] y haga clic en **[!UICONTROL Accept]** para continuar.

   Se requiere que cada usuario acepte las Condiciones de uso de la sesión. Este paso se repite para cada sesión iniciada.

   ![Tablero de análisis de todo el sitio](../../assets/tools/swat-tos.png)
   *Condiciones de uso*

1. En la parte superior del tablero, haga clic en la ficha que desee ver.

   ![Tablero de análisis de todo el sitio](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]información*

## Paso 3: Generar informe

1. En la esquina superior derecha del tablero, haga clic en **[!UICONTROL Generate Report]**.

1. Seleccione la casilla de verificación de cada **[!UICONTROL Type]** y **[!UICONTROL Priority]** que desea incluir en el informe.

1. Haga clic **[!UICONTROL Generate Report]**.

   ![Tablero de análisis de todo el sitio](../../assets/tools/swat-report-settings.png)
   *Configuración de informes*

| TAB | DESCRIPCIÓN |
| --- | --- |
| Panel | Muestra el estado del sistema con las notificaciones y recomendaciones actuales por prioridad. |
| Información | Proporciona información de contacto del cliente y un resumen de los tickets actuales, con información detallada sobre cada producto de Adobe Commerce instalado. |
| Recommendations | Enumera las recomendaciones basadas en prácticas recomendadas para abordar los problemas detectados en el sitio. |
| Excepciones | Enumera los errores lanzados por la aplicación debido a condiciones anormales sin un controlador de error. |
| Extensiones | Enumera todas las extensiones de terceros y bibliotecas de terceros. |

>[!NOTE]
>
>Después de aplicar una recomendación, puede que pasen unos días hasta que se actualice en la variable [!DNL Site-Wide Analysis Tool] Tablero o informe generado.
