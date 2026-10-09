---
title: 'ACSD-49179: el informe Pedidos muestra importes incorrectos para diferentes tiendas.'
description: Aplique el parche ACSD-49179 para corregir el problema de Adobe Commerce en el que el informe de pedidos muestra importes incorrectos en el caso de monedas diferentes para tiendas diferentes.
feature: Admin Workspace, Orders
role: Admin
exl-id: b10653ef-c4b1-40df-8bfe-7da755db621b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 4%
---
# ACSD-49179: el informe Pedidos muestra importes incorrectos para diferentes tiendas

El parche de ACSD-49179 corrige el problema en el que el informe de pedidos muestra cantidades incorrectas en caso de que haya diferentes monedas para diferentes tiendas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28. El ID del parche es ACSD-49179. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
