---
title: "ACSD-48773: La plantilla de correo electrónico de puntos de recompensa se ha tomado de una tienda incorrecta"
description: Aplique el parche ACSD-48773 para solucionar el problema de Adobe Commerce donde la plantilla de correo electrónico de puntos de recompensa se toma de la tienda incorrecta.
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-48773: la plantilla de correo electrónico de puntos de recompensa se ha tomado de una tienda incorrecta

El parche ACSD-48773 soluciona el problema de que la plantilla de correo electrónico de puntos de recompensa se toma de la tienda incorrecta. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26. El ID del parche es ACSD-48773. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El reíndice de precios del producto no funciona si el producto del paquete no está asignado a ningún sitio web.

<u>Pasos a seguir</u>:

1. Cree 2 sitios web, 2 tiendas y 2 vistas de tiendas.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]** y habilite **[!UICONTROL Reviews]**.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**.
Cambie a **[!DNL default website scope]** y establezca la dirección **[!UICONTROL Customer Support Sender Email]** (por ejemplo: *support_base@example.com*).
Cambie a **[!DNL second website scope]** y establezca la dirección **[!UICONTROL Customer Support Sender Email]** en otro valor (por ejemplo: *support_second@example.com*).
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]** y establezca **[!UICONTROL Share Customer Accounts]** = *Por sitio web*.
1. En **[!UICONTROL Reward Points]**, establezca lo siguiente:
   **[!UICONTROL Enable Reward Points Functionality]** = *Sí*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *Sí*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** y establecer **[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** y establecer **[!UICONTROL Email Sender]** = *Atención al cliente*
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** y configure las tasas de cambio del segundo sitio web para **[!UICONTROL Points/Currency]** y **[!UICONTROL Currency/Points]**.
1. Cree una cuenta de cliente en el segundo sitio web.
1. Inicie sesión como cliente en el segundo sitio web.
1. Asegúrese de habilitar **[!UICONTROL Subscribe]** para **[!UICONTROL Balance Updates]**.
1. Enviar una crítica del producto.
1. Vaya a **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**.
1. Cambiar el estado de la nueva revisión a ***[!UICONTROL Approved]*** y **[!UICONTROL Save]**.
1. Espere a que llegue el correo electrónico.

<u>Resultados esperados</u>:

El correo electrónico de actualización de puntos de recompensa debería haber sido enviado por el remitente del correo electrónico configurado en el segundo ámbito del sitio web.

<u>Resultados reales</u>:

El correo electrónico de actualización de puntos de recompensa lo envió el remitente de correo electrónico configurado en el ámbito predeterminado del sitio web.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
