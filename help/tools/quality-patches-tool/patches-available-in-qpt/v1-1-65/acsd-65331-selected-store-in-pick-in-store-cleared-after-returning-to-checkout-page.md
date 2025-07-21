---
title: 'ACSD-65331: el almacén seleccionado en [!UICONTROL Pick in Store] se borró después de volver al cierre de compra'
description: Aplique el parche ACSD-65331 para corregir el problema de Adobe Commerce en el que la opción [!UICONTROL Pick In Store] de la tienda seleccionada se borra cuando los usuarios regresan repetidamente a la página de cierre de compra.
feature: Inventory
role: Admin, Developer
type: Troubleshooting
exl-id: 10aaf898-feca-4485-90f6-6b3a9ea013b2
source-git-commit: dc5df9e918adffe8d6901478a676d9da36b33bcc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-65331: el almacén seleccionado en **[!UICONTROL Pick in Store]** se borró después de volver al cierre de compra

La revisión ACSD-65331 corrige el problema en el que el almacén seleccionado en la opción **[!UICONTROL Pick In Store]** se borra cuando los usuarios regresan repetidamente a la página de cierre de compra. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. El ID del parche es ACSD-65331. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El almacén seleccionado bajo la opción **[!UICONTROL Pick In Store]** se borra cuando los usuarios regresan repetidamente a la página de cierre de compra.

<u>Pasos a seguir</u>:

1. Para habilitar **[!UICONTROL In-Store Delivery]**, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Para configurar una clave de API [!DNL Google] válida para [!UICONTROL Google Distance Provider], vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]** para agregar un nuevo origen con los siguientes detalles:

   * **[!UICONTROL Latitude]**: *41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *Sí*
   * **[!UICONTROL Country]**: *Estados Unidos*
   * **[!UICONTROL State]**: *Illinois*
   * **[!UICONTROL City]**: *Secuencia de villancicos*
   * **[!UICONTROL Street]**: *565 E. Fullerton Ave.*
   * **[!UICONTROL Postcode]**: *60188*

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Stocks]** > **[!UICONTROL Add New Stock]** para crear un nuevo inventario de existencias.

   Asigne el origen recién creado y el sitio web principal a este inventario.
1. Edite cualquier producto de y:

   1. Asígnelo al origen recién creado.
   1. Establezca su estado en *[!UICONTROL In Stock]* y la cantidad en mayor que 0.

1. Ejecute los reindexadores.
1. En la tienda, cree un nuevo cliente y establezca una dirección de California como dirección de facturación y envío predeterminada.
1. Agregar una dirección de Illinois adicional al mismo cliente (no predeterminada).
1. Agregue el producto configurado al carro de compras y continúe con **[!UICONTROL Checkout]**.
1. Seleccione la dirección de Illinois, elija **[!UICONTROL Pick In Store]** como método de envío y haga clic en **[!UICONTROL Next]**.
1. Espere a que se cargue el origen y haga clic en **[!UICONTROL Next]**.
1. Vuelva a la página principal.
1. Vuelva a visitar la página **[!UICONTROL Checkout]**.

<u>Resultados esperados</u>:

La tienda seleccionada debe permanecer disponible en **[!UICONTROL Pick In Store]**.

<u>Resultados reales</u>:

El paso de envío comienza a cargarse y redirige a **[!UICONTROL Pick In Store]**, pero no hay ningún almacén visible.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
