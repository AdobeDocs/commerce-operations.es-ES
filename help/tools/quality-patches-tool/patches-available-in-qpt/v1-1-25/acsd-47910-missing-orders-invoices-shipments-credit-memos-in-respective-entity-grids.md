---
title: "ACSD-47910: pedidos, facturas, envíos y notas de abono que faltan en las cuadrículas de entidades respectivas"
description: Aplique el parche ACSD-47910 para solucionar el problema de Adobe Commerce en el que faltan pedidos, facturas, envíos y notas de abono en las cuadrículas de entidades correspondientes.
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47910: faltan pedidos, facturas, envíos y notas de abono en las cuadrículas de entidades correspondientes

El parche ACSD-47910 corrige el problema en el que faltan pedidos, facturas, envíos y notas de abono en las cuadrículas de entidades correspondientes. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25. El ID del parche es ACSD-47910. La versión en la que se solucionará este problema aún no está disponible.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.4-p1

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Faltan pedidos, facturas, envíos y notas de abono en las respectivas cuadrículas de entidades.

<u>Pasos a seguir</u>:

1. Habilitar **[!UICONTROL Asynchronous indexing]** en **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**.
1. Haz dos pedidos.
1. Ejecute el cron para sincronizar esos pedidos con la cuadrícula.
1. Abra uno de los pedidos y prepárelo para facturarlo. NO ENVIAR LA FACTURA AÚN.
1. Haga un nuevo pedido listo para colocarlo en el front-end. NO HAGA CLIC AÚN EN EL BOTÓN REALIZAR PEDIDO.
1. Agregar un `sleep(30)` en `foreach` a las `NotSyncedDataProvider::L43`.
1. Ejecutar `bin/magento cron:run`.
1. Ahora coloque el nuevo pedido.
1. Facturar el pedido anterior.
1. Vuelva a ejecutar el cron esperando que se sincronice el nuevo orden.
1. Vaya a la cuadrícula de pedidos en Admin.

<u>Resultados esperados</u>:

El nuevo orden debe aparecer en la cuadrícula del orden.

<u>Resultados reales</u>:

La actualización de pedido anterior se sincronizó con la cuadrícula (**[!UICONTROL status: Processing]**). El nuevo orden nunca aparece en la cuadrícula.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
