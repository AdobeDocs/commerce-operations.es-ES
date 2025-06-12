---
title: 'ACSD-48362: se utiliza la dirección de envío predeterminada en lugar de una nueva.'
description: Aplique el parche ACSD-48362 para solucionar el problema de Adobe Commerce en el que se utiliza la dirección de envío predeterminada en lugar de una nueva al realizar un pedido con una oferta negociable.
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
exl-id: 6f0717a6-1e29-4059-9640-5b92586c36e4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# ACSD-48362: se utiliza la dirección de envío predeterminada en lugar de una nueva

El parche ACSD-48362 corrige el problema en el que se utiliza la dirección de envío predeterminada en lugar de la dirección recién agregada al realizar un pedido utilizando una cotización negociable. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27. El ID del parche es ACSD-48362. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se utiliza la dirección de envío predeterminada en lugar de la dirección de envío recién agregada al realizar un pedido con una oferta negociable.

<u>Pasos a seguir</u>:

1. Para habilitar el presupuesto B2B, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**.
1. Inicie sesión como usuario de la empresa.
1. Añadir un producto al carro de compras.
1. Vaya a la página del carro de compras y solicite un presupuesto.
1. Vaya a la página **[!UICONTROL My Quotes]** del cliente y seleccione la oferta que acaba de crear.
1. Vaya a la sección **[!UICONTROL Shipping Information]** de la página del presupuesto del cliente.
   * Haga clic en **[!UICONTROL Add New Address]**, rellene el formulario y guarde la dirección (no seleccione **[!UICONTROL Use as my default billing address]** ni **[!UICONTROL Use as my default shipping address]**).
1. Haga clic en **[!UICONTROL Send for Review]** en la página de presupuesto del cliente.
1. Vaya al Administrador de Adobe Commerce como usuario administrador, abra la oferta que acaba de crear y haga clic en **[!UICONTROL Send]**.
1. Ahora ve a la página de presupuesto del cliente, actualiza la página y haz clic en **[!UICONTROL Proceed to Checkout]**.
1. En la página de pago y envío, los datos muestran la dirección de envío predeterminada incluso cuando se selecciona la nueva dirección de envío.
1. Haga clic en **[!UICONTROL Continue]** y realice el pedido.

<u>Resultados esperados</u>:

El pedido debe utilizar la nueva dirección sin volver a seleccionar la dirección de envío predeterminada en la página de cierre de compra.

<u>Resultados reales</u>:

El pedido se realiza con la dirección de envío predeterminada.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube. 

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
