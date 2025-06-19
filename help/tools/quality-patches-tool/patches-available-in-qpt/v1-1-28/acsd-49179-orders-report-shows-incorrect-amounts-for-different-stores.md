---
title: 'ACSD-49179: el informe Pedidos muestra importes incorrectos para diferentes tiendas.'
description: Aplique el parche ACSD-49179 para corregir el problema de Adobe Commerce en el que el informe de pedidos muestra importes incorrectos en el caso de monedas diferentes para tiendas diferentes.
feature: Admin Workspace, Orders
role: Admin
exl-id: b10653ef-c4b1-40df-8bfe-7da755db621b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-49179: el informe Pedidos muestra importes incorrectos para diferentes tiendas

El parche de ACSD-49179 corrige el problema en el que el informe de pedidos muestra cantidades incorrectas en caso de que haya diferentes monedas para diferentes tiendas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28. El ID del parche es ACSD-49179. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El informe de pedidos muestra importes incorrectos en el caso de monedas diferentes para tiendas diferentes.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** y establezca [!UICONTROL Catalog Price Scope] = [!UICONTROL Website].
1. Cree un sitio web, una tienda y una vista de tienda adicionales.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL General]** > **[!UICONTROL Currency Setup]** > **[!UICONTROL Currency Options]** y establezca:
   * Configuración predeterminada:
      * Moneda base: USD
      * Divisa para mostrar predeterminada: USD
      * Monedas permitidas: EUR, USD y THB (Thai Baht)
   * Sitio web principal:
      * Moneda base: EUR
      * Divisa para mostrar predeterminada: EUR
      * Monedas permitidas: EUR
   * Nuevo sitio web adicional:
      * Moneda base: THB (Baht tailandés)
      * Moneda de visualización predeterminada: THB (Baht tailandés)
      * Monedas permitidas: THB (Thai Baht)
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Currency]** > **[!UICONTROL Currency Rates]** y establezca las tasas de conversión vacías para THB (establezca las tasas en 1.0000).
1. Cree un producto, asígnelo a ambos sitios web y realice un pedido con este producto en el sitio web adicional creado anteriormente.
1. Asegúrese de que el pedido esté en estado *Procesando* (facturarlo).
1. En el servidor, vaya a **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Haga clic en la advertencia **[!UICONTROL Yellow]** para actualizar las estadísticas.
1. Establezca el ámbito del informe en el sitio web adicional creado anteriormente y establezca el filtro de la siguiente manera:
   * [!UICONTROL Date Used]: [!UICONTROL Created]
   * [!UICONTROL Period]: [!UICONTROL Day]
   * [!UICONTROL From and To]: el mismo día en que se realizó el pedido de prueba
   * [!UICONTROL Order Status]: [!UICONTROL Any]
   * [!UICONTROL Empty rows]: [!UICONTROL No]
   * [!UICONTROL Show Actual Values]: [!UICONTROL No]

<u>Resultados esperados</u>:

El total de ventas muestra la cantidad correcta convertida a la moneda del sitio web.

<u>Resultados reales</u>:

El total es cero.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
