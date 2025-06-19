---
title: 'ACSD-48570: solucionando el problema de vínculo de contraseña de restablecimiento de administrador con el código de tienda en la URL'
description: Aplique el parche ACSD-48570 para corregir el problema de Adobe Commerce en el que no se pudo acceder a la página de restablecimiento de contraseña a través del vínculo de restablecimiento de contraseña de administrador cuando se habilitó la configuración de [!UICONTROL Add Store Code to URLs].
feature: Security, User Account
role: Admin, Developer
exl-id: 049a82ff-80e3-46a1-8472-ac74de0e365f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48570: solucionando el problema de vínculo de contraseña de restablecimiento de administrador con el código de tienda en la URL

Revisión de ACSD-48570 para solucionar el problema de Adobe Commerce en el que no se podía acceder a la página de restablecimiento de contraseña a través del vínculo de restablecimiento de contraseña de administrador cuando la configuración de *[!UICONTROL Add Store Code to URLs]* estaba habilitada. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. El ID del parche es ACSD-48570. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando la configuración **[!UICONTROL Add Store Code to URLs]** está habilitada, la funcionalidad de restablecimiento de contraseña del administrador no funciona correctamente.
Cuando un usuario administrador solicita un restablecimiento de contraseña y hace clic en el vínculo de recuperación del correo electrónico, se le redirige a la página de inicio de sesión o recibe un error 404 en lugar de que se le redirija al formulario de restablecimiento de contraseña. Esto evita que los administradores recuperen sus cuentas sin intervención manual.

<u>Pasos a seguir</u>:

1. Habilite la configuración de **[!UICONTROL Add Store Code to URLs]** en **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL URL Options]**.
1. Cierre la sesión en el panel de administración y haga clic en el vínculo **[!UICONTROL Forgot your password?]** de la página de inicio de sesión de administración.
1. Introduzca el correo electrónico del usuario administrador, pase el captcha y haga clic en **[!UICONTROL Retrieve Password]**.
1. Abra el correo electrónico de restablecimiento de contraseña y haga clic en el enlace de recuperación de contraseña.

<u>Resultados esperados</u>:

Se debe mostrar el formulario para restablecer la contraseña.

<u>Resultados reales</u>:

Se muestra la página de inicio de sesión o una página de error 404 en lugar del formulario de restablecimiento de contraseña.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
