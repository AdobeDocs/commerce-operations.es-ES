---
title: 'ACSD-53309: aplicación de impuestos incompleta para opciones personalizables y etiqueta [!UICONTROL Regular Price]'
description: Aplique el parche ACSD-53309 para corregir el problema de Adobe Commerce en el que los impuestos no se aplican completamente en la etiqueta '[!UICONTROL Regular Price]' cuando se selecciona una opción personalizable.
feature: Taxes, Shipping/Delivery
role: Admin, Developer
exl-id: 7f4a8923-11dd-48b2-9d97-77de5c2b24ce
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 42e094d8-211b-5acf-b52f-d8979151ab30
    internal-label: Taxes
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 20%
---
# ACSD-53309: aplicación de impuestos incompleta para opciones personalizables y etiqueta &#39;[!UICONTROL Regular Price]&#39;

La revisión ACSD-53309 corrige el problema en el que los impuestos no se aplican completamente en la etiqueta &#39;[!UICONTROL Regular Price]&#39; cuando se selecciona una opción personalizable. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.43. El ID del parche es ACSD-53309. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El impuesto no se refleja completamente en la etiqueta &#39;[!UICONTROL Regular Price]&#39; cuando se elige una opción personalizable.

<u>Pasos a seguir</u>:

1. Inicie sesión en el panel de administración.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** para establecer la configuración de impuestos.

   * [!UICONTROL Tax Classes]:

     * [!UICONTROL Tax Class for Shipping] = [!UICONTROL Taxable Goods]
     * [!UICONTROL Tax Class for Gift Options] = [!UICONTROL Taxable Goods]

   * [!UICONTROL Calculation Settings]:

     * [!UICONTROL Catalog Prices] = [!UICONTROL Including Tax]
     * [!UICONTROL Shipping Prices] = [!UICONTROL Including Tax]
     * [!UICONTROL Apply Discount On Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Default Tax Destination Calculation]:

     * [!UICONTROL Default Post Code] = *

   * [!UICONTROL Price Display Settings]:

     * [!UICONTROL Display Product Prices In Catalog] = [!UICONTROL Including Tax]
     * [!UICONTROL Display Shipping Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Shopping Cart Display Settings]:

     * [!UICONTROL Display Prices] = [!UICONTROL Including Tax]
     * [!UICONTROL Display Subtotal] = [!UICONTROL Including Tax]
     * [!UICONTROL Display Shipping Amount] = [!UICONTROL Including Tax]

1. Conjunto **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** > **[!UICONTROL Country]** = *Reino Unido*.

1. Crear los(as) siguientes *[!UICONTROL Tax Rate]* y *[!UICONTROL Tax Rules]*:

   * [!UICONTROL Country] = Estados Unidos
   * [!UICONTROL Zip Code] = *
   * [!UICONTROL State] = *
   * [!UICONTROL Rate] = 20%
1. Cree un producto sencillo y configure lo siguiente:
   * [!UICONTROL Price = 110]
   * [!UICONTROL Special Price = 100]
   * En la lista desplegable, establezca el tipo en opción personalizada con el precio establecido en 15 %
1. Vaya a la página del producto para ver el artículo simple hecho en la tienda.
1. Elija la opción personalizada creada, *15%*.

<u>Resultados esperados</u>:

* El 20 % de impuesto se aplica a la opción personalizada seleccionada.
* &#39;[!UICONTROL Regular Price]&#39; = 151.80.

<u>Resultados reales</u>:

* El 20 % de impuesto no se aplica a la opción personalizada seleccionada.
* &#39;[!UICONTROL Regular Price]&#39; = 148.50.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
