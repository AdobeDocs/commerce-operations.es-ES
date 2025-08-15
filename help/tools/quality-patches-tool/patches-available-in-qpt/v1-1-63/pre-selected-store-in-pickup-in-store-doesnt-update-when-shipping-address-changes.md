---
title: 'ACSD-64753: La tienda preseleccionada en la tienda de recogida no se actualiza cuando se producen cambios en la dirección de envío'
description: Aplique el parche ACSD-64753 para solucionar el problema de Adobe Commerce en el que la tienda preseleccionada no se actualizaba cuando se introducía una nueva dirección de envío fuera del radio de servicio de la tienda seleccionada.
feature: Inventory
role: Admin, Developer
exl-id: 4efc99d6-88a3-43f9-88d4-dedb9d8a269e
type: Troubleshooting
source-git-commit: 036c1b81d9ec8f55f002446a8ea6078c6f8014d9
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-64753: La tienda preseleccionada en &quot;Recogida en tienda&quot; no se actualiza cuando se producen cambios en la dirección de envío

El parche de ACSD-64753 soluciona el problema de que la tienda preseleccionada no se actualizaba cuando se introducía una nueva dirección de envío fuera del radio de servicio de la tienda seleccionada. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63. El ID del parche es ACSD-64753. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La tienda preseleccionada no se actualizó cuando se introdujo una nueva dirección de envío fuera del radio de servicio de la tienda seleccionada.

<u>Pasos a seguir</u>:

1. Para habilitar **[!UICONTROL In-Store Delivery]**, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Proporcione una clave de API [!DNL Google] válida para [!DNL Google Distance Provider]. Para ello, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**.
1. Agregue un nuevo origen (**[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]**) y establezca los siguientes valores:
   * **[!UICONTROL Latitude]**: *-41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *Sí*
   * **[!UICONTROL Country United]**: *Estados*
   * **[!UICONTROL State]**: *Illinois*
   * **[!UICONTROL City]**: *Secuencia de villancicos*
   * **[!UICONTROL Postcode]**: *60188*
1. Agregue un nuevo inventario de existencias (**[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** > **[!UICONTROL Add New Stock]**) y asígnele el nuevo origen y el sitio web principal.
1. Edite cualquier producto, asigne el producto al nuevo Source, En stock y cantidad > *0*.
1. Espere hasta que se complete la reindexación.
1. En la tienda, cree un nuevo cliente y, a continuación, agregue una dirección de California como facturación y envío predeterminados.
1. Agregue otra dirección de Illinois no predeterminada a este cliente.
1. Añada el producto al carro de compras y continúe con el cierre de compra.
1. Deje seleccionada la dirección de envío de California y elija **[!UICONTROL Pick in Store]** método de envío. Haga clic en **[!UICONTROL Next]**.

<u>Resultados esperados</u>:

Dado que la dirección de California está fuera del radio máximo de búsqueda (200 km), el Source de Illinois no debe estar disponible para el cliente.

<u>Resultados reales</u>:

Se puede seleccionar la fuente de Illinois y el cliente puede continuar con el cierre de compra.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
