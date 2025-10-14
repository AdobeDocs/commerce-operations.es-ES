---
title: 'ACSD-52287: El estado de los pedidos archivados no cambia'
description: Aplique el parche ACSD-52287 para solucionar el problema de Adobe Commerce en el que el estado de los pedidos archivados no cambia de *completado* a *cerrado* en la cuadrícula después de enviar la nota de crédito.
feature: Orders, Checkout
role: Admin, Developer
exl-id: 012f49ba-fdc1-4e1e-87fe-7b9c661f231b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-52287: El estado de los pedidos archivados no cambia

El parche ACSD-52287 corrige el problema en el que el estado de los pedidos archivados no cambia de *completados* a *cerrados* en la cuadrícula después de que se enviara el abono. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.38. El ID del parche es ACSD-52287. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado de los pedidos archivados no cambia de *completados* a *cerrados* en la cuadrícula después de que se haya enviado el abono.

<u>Pasos a seguir</u>:

1. Configurar *[!UICONTROL Asynchronous Indexing]*.
   * En la barra lateral de Administración, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * En el panel izquierdo, expanda la sección **[!UICONTROL Advanced]** y elija **[!UICONTROL Developer]** debajo.
   * Expanda la sección **[!UICONTROL Grid Settings]**.
   * Establezca *[!UICONTROL Asynchronous indexing]* en *Sí*.
   * Haga clic en **[!UICONTROL Save Config]**.
1. Configure *[!UICONTROL Order Archive]*.
   * En la barra lateral de Administración, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * En el panel izquierdo, expanda la sección **[!UICONTROL Sales]** y elija **[!UICONTROL Sales]** debajo.
   * Expanda la sección **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]**.
   * Establezca *[!UICONTROL Enable Archiving]* en *Sí* (deje el resto de las configuraciones como predeterminadas).
   * Haga clic en **[!UICONTROL Save Config]**.
1. Realice un pedido en el front-end.
1. Ejecute [!DNL cron] para que aparezca en *[!UICONTROL Admin Order Grid]*.
1. Facturar y enviar el pedido para actualizar el estado del pedido a *Completo*.
1. Ejecute [!DNL cron] para actualizar *[!UICONTROL Sales Order Grid]* con el último estado de pedido.
1. Archivar el pedido.
1. Vaya a *[!UICONTROL Archived order grid]*.
1. Abra el pedido archivado y devuélvalo sin conexión creando un [!UICONTROL Credit Memo] para hacer el [!UICONTROL Order status]: *Cerrado*.
1. Ejecute [!DNL cron] varias veces.
1. Compruebe el *[!UICONTROL Archived order grid]* para ver el nuevo estado del pedido.

<u>Resultados esperados</u>:

El pedido se muestra como *Cerrado*.

<u>Resultados reales</u>:

El pedido se muestra como *Completo*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
