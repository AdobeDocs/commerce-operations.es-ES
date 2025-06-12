---
title: 'MDVA-39305-V3: problema de inicio de sesión con habilitado [!DNL Google reCAPTCHA]'
description: Aplique el parche de MDVA-39305-V3 para corregir el problema de Adobe Commerce en el que los clientes registrados no pueden iniciar sesión cuando  [!DNL Google reCAPTCHA] está habilitado. Este parche también soluciona el problema en el que un formulario se puede enviar antes de que  [!DNL Google reCAPTCHA] se cargue completamente. Además, corrige el error *Call to a member function isDisabled() en null* cuando los bloques se utilizan en ubicaciones no predeterminadas en una página de CMS.
feature: Console
role: Admin
exl-id: 63e880aa-9a2e-4c34-9ead-20bfc5204f2c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-39305-V3: problema de inicio de sesión con [!DNL Google reCAPTCHA] habilitado

>[!NOTE]
>
>Este parche es una actualización del parche [MDVA-39305](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-1/mdva-39305-login-issues-with-enabled-google-recaptcha.md).

El parche de MDVA-39305-V3 corrige el problema en el cual los clientes registrados no pueden iniciar sesión cuando [!DNL Google reCAPTCHA] está habilitado. Esta revisión también corrige el problema en el cual un formulario se puede enviar antes de que [!DNL Google reCAPTCHA] se cargue completamente. Además, corrige el error *Llamada a una función miembro isDisabled() en null* cuando los bloques se usan en ubicaciones no predeterminadas en una página de CMS.

Este parche se agregó en la versión [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48. Se actualizó en la versión 1.1.58 de QPT para incluir las nuevas versiones de Adobe Commerce 2.4.7 - 2.4.7-p4. La ID del parche es MDVA-39305-V3. Tenga en cuenta que el problema se corrigió en las versiones de Adobe Commerce 2.4.4, 2.4.5-p2 y 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4, 2.4.5-p2, 2.4.7

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p1 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problemas

### Caso I

1. Los clientes registrados no pueden iniciar sesión con el [!DNL Google reCAPTCHA] habilitado.
1. Se puede enviar un formulario antes de que [!DNL Google reCAPTCHA] se cargue completamente.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]** > **[!DNL Google reCAPTCHA Storefront]** y habilite ***[!DNL Google reCAPTCHA]***.
1. Vaya al front-end.
1. Abra **[!UICONTROL Developer Tool Console]** en el explorador.

<u>Resultados esperados</u>:

No hay advertencias de CSP en la consola.

<u>Resultados reales</u>:

Advertencias de CSP en la consola.

### Caso II

Se produce un error que indica *Call to a member function isDisabled() en null* cuando se usan bloques en ubicaciones no predeterminadas en una página de CMS.

<u>Pasos a seguir</u>:

1. Cree un bloque estático con el siguiente contenido:

   ```
   {{block class="Magento\Newsletter\Block\Subscribe" name="home.form.subscribe"
   template="Magento_Newsletter::subscribe.phtml"}}
   ```

1. Agregue un bloque estático a una página de CMS desde **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Add/Edit CMS page]** > **[!UICONTROL Content]**.
1. Guarde la página.

<u>Resultados esperados</u>:

La página se carga sin errores.

<u>Resultados reales</u>:

Se produce un error 500 en la página de la tienda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
