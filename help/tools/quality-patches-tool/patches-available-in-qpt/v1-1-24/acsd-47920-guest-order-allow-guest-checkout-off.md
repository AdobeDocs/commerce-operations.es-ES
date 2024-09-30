---
title: "ACSD-47920: un usuario invitado puede realizar pedidos a través de la API de REST incluso cuando [!UICONTROL Allow Guest Checkout] está desactivado"
description: Aplique el parche ACSD-47920 para corregir el problema de Adobe Commerce en el que los pedidos se pueden realizar mediante la API de REST como usuario invitado incluso cuando [!UICONTROL Allow Guest Checkout] está desactivado.
feature: REST, Checkout, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-47920: un usuario invitado puede realizar pedidos a través de la API de REST incluso cuando **[!UICONTROL Allow Guest Checkout]** está desactivado

El parche ACSD-47920 corrige el problema en el que los pedidos se pueden realizar mediante la API de REST como usuario invitado incluso cuando **[!UICONTROL Allow Guest Checkout]** está desactivado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24. El ID del parche es ACSD-47920. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los pedidos se pueden realizar mediante la API de REST como usuario invitado incluso cuando **[!UICONTROL Allow Guest Checkout]** está desactivado.

<u>Pasos a seguir</u>:

1. Vaya a Administración de Adobe Commerce > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > y establezca **[!UICONTROL Allow Guest Checkout]** en _No_.
1. Utilice la API de REST para añadir un producto al carro de compras y realizar un pedido.

<u>Resultados esperados</u>:

La API de cierre de compra de invitado devuelve un error *[!UICONTROL Sorry, guest checkout is not available]* si **[!UICONTROL Allow Guest Checkout]** está establecido en _No_.

<u>Resultados reales</u>:

La API de cierre de compra de invitado permite realizar un pedido aunque **[!UICONTROL Allow Guest Checkout]** esté establecido en _No_.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
