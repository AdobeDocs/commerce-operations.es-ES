---
title: '49843 ACSD: el vínculo de descarga de producto no está disponible después de facturarse automáticamente con [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'
description: Aplique el parche ACSD-49843 para solucionar el problema de Adobe Commerce en el que el vínculo de descarga de productos no está disponible después de que un método de pago en línea factura automáticamente el artículo pedido cuando [!UICONTROL Payment Action] se establece en [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: e990b550-fb32-48d2-9c39-2176d7ab34c9
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-49843: el vínculo de descarga de producto no está disponible después de facturarse automáticamente con [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

El parche ACSD-49843 corrige el problema en el que el vínculo de descarga del producto no está disponible después de que un método de pago en línea haya facturado automáticamente el elemento solicitado cuando [!UICONTROL Payment Action] está establecido en [!UICONTROL Intent Sale]. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.37. El ID del parche es ACSD-49843. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El vínculo de descarga de productos no está disponible después de que un método de pago en línea haya facturado automáticamente el artículo pedido cuando [!UICONTROL Payment Action] está establecido en [!UICONTROL Intent Sale].

<u>Pasos a seguir</u>:

1. Inicie sesión en Adobe Commerce Admin y vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * En la lista desplegable [!UICONTROL Payment Action], seleccione **[!UICONTROL Intent Sale]** y establezca *[!UICONTROL Enable Card Payments]* en *Sí*.

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]** y asegúrese de que está establecido en *&quot;Facturado&quot;*.
1. En la tienda, inicie sesión como cliente.

   * Añada cualquier producto descargable y un producto simple al carro de compras.
   * Use [!DNL Braintree Pay] para hacer el pedido con la opción de tarjeta.

1. Vaya a **[!UICONTROL My Orders]** y compruebe que la factura se crea automáticamente para el pedido y que ambos estados de artículo son *&quot;Facturado&quot;*.
1. Vaya a **[!UICONTROL My Downloadable Products]** y observe que el vínculo de descarga aún no está disponible.
1. En el Administrador, vaya a ese pedido y cree un envío para él.
1. En la tienda, vaya a **[!UICONTROL My Downloadable Products]** y observe que el vínculo de descarga ya está disponible.

<u>Resultados esperados</u>:

El vínculo de descarga está disponible cuando el estado del producto descargable es *&quot;Facturado&quot;*.

<u>Resultados reales</u>:

El vínculo de descarga no está disponible aunque el estado del producto descargable indique *&quot;Facturado&quot;*. Solo está disponible después de crear un envío para el producto físico.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
