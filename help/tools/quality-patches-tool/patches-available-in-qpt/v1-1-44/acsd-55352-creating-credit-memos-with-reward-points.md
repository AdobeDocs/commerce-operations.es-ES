---
title: 'ACSD-55352: Creación de notas de crédito con puntos de recompensa'
description: Aplique el parche ACSD-55352 para solucionar el problema de Adobe Commerce en el que, después de crear una nota de crédito parcial con puntos de recompensa del cliente, el estado del pedido cambia a *cerrado* y las opciones de nota de crédito desaparecen de la página de orden del administrador.
feature: Checkout, Orders
role: Admin, Developer
exl-id: bee0c4be-11ec-4dcb-9b3c-7af26676cee9
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-55352: Creación de notas de crédito con puntos de recompensa

El parche ACSD-55352 corrige el problema por el cual, después de crear un abono parcial con puntos de recompensa del cliente, el estado del pedido cambia a *cerrado* y las opciones de abono desaparecen de la página de pedidos del administrador. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44. El ID del parche es ACSD-55352. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Después de crear un abono parcial con puntos de recompensa del cliente, el estado del pedido cambia a *cerrado* y las opciones de abono desaparecen de la página de pedidos del administrador.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador de Adobe Commerce.
2. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. Añada dos tarifas:
   * *[!UICONTROL First]*:
      * *[!UICONTROL Direction]* = *Puntos por la moneda*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*:
      * *[!UICONTROL Direction]* = *Divisa a puntos*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. Crea un producto simple con el precio de *$100* y con *Cantidad*: *100*.
5. Cree un cliente desde la tienda.
6. Vuelva al servidor : **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > Agregar *100* y guarde el cliente.
7. Vaya a la tienda e inicie sesión como el cliente creado anteriormente.
8. Agregar el producto al carro con *Cantidad* : *10*.
9. Vaya a **[!UICONTROL Checkout]** y use los *100* puntos de recompensa disponibles cuando se le solicite y haga el pedido.
10. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** y envíe ese pedido.
11. Vaya a [!UICONTROL Credit Memo] y actualice la *cantidad de reembolso* a *8*.
12. Marque la casilla **[!UICONTROL Refund Reward Points]** y haga clic en **[!UICONTROL Refund offline]**.
13. Intente reembolsar los otros dos productos restantes del pedido utilizando [!UICONTROL Credit Memo].

<u>Resultados esperados</u>:

* El administrador crea [!UICONTROL Credit Memo] para devolver los dos productos restantes.
* El estado del pedido es *Completado*.

<u>Resultados reales</u>:

* No se puede crear más [!UICONTROL Credit Memo].
* El estado del pedido es *Cerrado*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
