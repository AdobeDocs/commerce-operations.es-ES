---
title: "ACSD-46617: el botón **[!UICONTROL Continue to Checkout]** aparece atenuado cuando el subtotal es mayor que la cantidad mínima de pedido configurada"
description: Aplique el parche ACSD-46617 para resolver el problema de Adobe Commerce donde el botón **[!UICONTROL Continue to Checkout]** aparece atenuado aunque el subtotal sea mayor que la cantidad mínima de pedido configurada.
feature: Checkout, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-46617: botón &quot;[!UICONTROL Continue to Checkout]&quot; atenuado cuando el subtotal es mayor que &quot;[!UICONTROL Minimum Order Amount]&quot;

Este parche de ACSD-46617 resuelve el problema en el que el botón **[!UICONTROL Continue to Checkout]** aparece atenuado incluso si el subtotal es mayor que la cantidad de pedido mínima configurada. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24. El ID del parche es ACSD-46617. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El botón **[!UICONTROL Continue to Checkout]** aparece atenuado incluso si el subtotal es mayor que la cantidad mínima de pedido configurada.

<u>Pasos a seguir</u>:

1. Vaya a Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** y establezca lo siguiente:
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * 
     [!UICONTROL Minimum Amount]: *2*

1. Crear un [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * 
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. Cree un producto con el precio de 25 $.
1. Añadir el producto al carro de compras.
1. Vaya al carro de compras, seleccione el método de $5 **[!UICONTROL Flat Rate shipping]** y aplique el código de cupón.
1. Vaya al cierre de compra, complete el envío y vaya a la sección **[!UICONTROL Paytment]**.
1. Vuelva al carro de compras.

<u>Resultados esperados</u>:

No hay ningún error relacionado con la cantidad mínima del pedido, ya que el total general de 2,4 dólares es mayor que el importe requerido de 2 dólares.

<u>Resultados reales</u>:

* Hay un error relacionado con la cantidad mínima del pedido, incluso cuando el total general de 2,4 $ es mayor que la cantidad mínima del pedido de 2 $.
* El botón **[!UICONTROL Continue to Checkout]** está atenuado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
