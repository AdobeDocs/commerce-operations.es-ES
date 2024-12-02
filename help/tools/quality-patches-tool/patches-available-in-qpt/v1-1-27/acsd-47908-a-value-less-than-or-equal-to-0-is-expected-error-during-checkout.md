---
title: 'ACSD-47908: *Se espera un valor menor o igual a 0* error durante el cierre de compra'
description: Aplique el parche ACSD-47908 para corregir el error de Adobe Commerce *Se espera un valor menor o igual a 0* al seleccionar el origen y la cantidad en el paso de envío durante el cierre de compra.
feature: Admin Workspace, Checkout, Orders
role: Admin
exl-id: f1429bd9-652d-43c0-af52-b2258e2a7643
source-git-commit: f6abbbb28a3077f7bf26a393388c5059fcd8c599
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ACSD-47908: *Se espera un valor menor o igual que 0* error durante la desprotección

La revisión ACSD-47908 corrige el error *Se espera un valor menor o igual a 0* al seleccionar el origen y la cantidad en el paso de envío durante el cierre de compra. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27. El ID del parche es ACSD-47908. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se genera el siguiente error al seleccionar el origen y la cantidad en el paso de envío durante la desprotección: *Se espera un valor inferior o igual a 0*.

<u>Requisitos previos</u>:

Instale los módulos de Adobe Commerce Inventory management (MSI).

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** y configure varios orígenes.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** y cree un nuevo inventario de existencias.
   * Ahora asigne las fuentes al nuevo stock.
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** y edite al menos un producto.
   * Asegúrese de que los productos estén asignados a los nuevos orígenes y especifique la cantidad disponible.
1. Vaya a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** y cree un nuevo pedido.
1. Agregue esos productos al pedido y colóquelo.
1. Haga clic en **[!UICONTROL Ship]**.
1. Seleccione el origen desde el que desea realizar el envío.
1. Especifique la cantidad de cada artículo que desea enviar.
1. Vuelva a cargar la página.
1. Haga clic en **[!UICONTROL Proceed to Shipment]**.

<u>Resultados esperados</u>:

La nueva página de envío se abre sin ningún error.

<u>Resultados reales</u>:

* No se puede validar la cantidad introducida.
* Se produjo el siguiente error: *Escriba un valor menor o igual que 0*.

  Sin embargo, el error es incoherente y puede no aparecer siempre.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
