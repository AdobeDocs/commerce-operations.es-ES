---
title: Cómo acceder a  [!DNL Site-Wide Analysis Tool]
description: Obtenga información sobre cómo acceder al panel de herramientas de análisis de todo el sitio desde el Panel de administración de Adobe Commerce. Descubra los permisos de usuario y los requisitos de funciones.
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# Cómo acceder a [!DNL Site-Wide Analysis Tool]

Puede acceder al tablero [!DNL Site-Wide Analysis Tool] desde el [!UICONTROL Admin Panel] de su tienda.

El servicio [!DNL Site-Wide Analysis Tool] está disponible en [modo de producción](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#operation-modes) para [!UICONTROL Admin] usuarios con permiso para obtener acceso al usuario [recursos de rol](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles).

>[!NOTE]
>
>Efectivo el 23 de abril de 2024, [!DNL Site-Wide Analysis Tool] se ha retirado del mercado y ya no está disponible para los clientes locales de Adobe Commerce.


![Panel de análisis de todo el sitio](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]panel*

>[!NOTE]
>
>Su cuenta debe tener derecho a **[!DNL Support Permissions]** para tener acceso a [!DNL Site-Wide Analysis Tool Dashboard].
>>Consulta más detalles en [Compartir una [!DNL Commerce] cuenta](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) en nuestra guía de usuario.

## Iniciando sesión en [!DNL Site-Wide Analysis Tool Dashboard] desde [!UICONTROL Admin Panel] de su tienda

### Paso 1: Verificar los permisos

Compruebe que la cuenta de usuario [!UICONTROL Admin] tiene permiso para obtener acceso a [!DNL Site-Wide Analysis Tool] a través de su [función de usuario asignada](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles).

>[!IMPORTANT]
>
>El recurso de rol [!DNL Site-Wide Analysis Tool] (permiso) está **no** asignado automáticamente. DEBE activarse para el rol de usuario y el rol asignado individualmente a cada cuenta de usuario en [!UICONTROL Admin].

Para la función personalizada que necesita acceso de [!DNL Site-Wide Analysis Tool], haga lo siguiente:

1. Seleccione el recurso de rol **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Panel de análisis de todo el sitio](../../assets/tools/swat-role-access.png)
   Se ha seleccionado el permiso *[!DNL Site-Wide Analysis Tool]para el rol*

1. Haga clic en **[!UICONTROL Save Role]**.

1. Notifique a los usuarios que tengan asignada esa función que cierren la sesión de [!DNL Admin] y que vuelvan a iniciarla.

>[!NOTE]
>
>Si ha comprobado que la cuenta de usuario tiene permiso para acceder a [!DNL Site-Wide Analysis Tool] y el usuario recibe un error 403 al intentar acceder a la herramienta desde [!UICONTROL Admin], su instancia de Adobe Commerce en la infraestructura en la nube podría tener habilitado el control de acceso HTTP. El panel [!DNL Site-Wide Analysis Tool] NO es compatible si tiene habilitada la autenticación HTTP. Para obtener más información sobre cómo resolver este problema, consulte nuestro [artículo de asistencia](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/403-errors-when-accessing-site-wide-analysis-tool-on-magento).

### Paso 2: Acceso a [!DNL Site-Wide Analysis Tool]

1. En la barra lateral *[!UICONTROL Admin]*, vaya a **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Panel de análisis de todo el sitio](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]ubicación en [!UICONTROL Admin Panel] en Adobe Commerce*

1. Lea las *Condiciones de uso* de [!DNL Site-Wide Analysis Tool] y haga clic en **[!UICONTROL Accept]** para continuar.

   Cada usuario debe aceptar las Condiciones de uso de la sesión. Este paso se repite en cada sesión iniciada.


1. En la parte superior del panel, haga clic en la pestaña que desee ver.

   ![Panel de análisis de todo el sitio](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]información*

## Generar informes desde [!DNL Site-Wide Analysis Tool Dashboard]

1. En la esquina superior derecha del panel, haga clic en **[!UICONTROL Generate Report]**.

1. Seleccione la casilla de verificación de cada configuración de **[!UICONTROL Type]** y **[!UICONTROL Priority]** que desee incluir en el informe.

1. Haga clic en **[!UICONTROL Generate Report]**.

   ![Panel de análisis de todo el sitio](../../assets/tools/swat-report-settings.png)
   *Configuración de informe*

| TABULACIÓN | DESCRIPCIÓN |
| --- | --- |
| Tablero | Muestra el estado del sistema con las notificaciones y recomendaciones actuales por prioridad. |
| Información | Proporciona información de contacto del cliente y un resumen de los tickets actuales, con información detallada sobre cada producto de Adobe Commerce instalado. |
| Recommendations | Enumera recomendaciones basadas en prácticas recomendadas para abordar los problemas detectados en el sitio. |
| Excepciones | Enumera los errores producidos por la aplicación debido a condiciones anómalas sin un controlador de errores. |
| Extensiones | Enumera todas las extensiones de terceros y bibliotecas de terceros. |

>[!NOTE]
>
>Después de aplicar una recomendación, es posible que tarden unos días en actualizarse en el [!DNL Site-Wide Analysis Tool Dashboard] o en el informe generado.
