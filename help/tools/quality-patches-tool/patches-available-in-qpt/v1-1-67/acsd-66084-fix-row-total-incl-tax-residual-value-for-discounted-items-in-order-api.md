---
title: 'ACSD-66084: "row_total_incl_tax" devuelve cerca de cero en lugar de 0,00 para artículos con descuento completo en la API de pedidos'
description: Aplique el parche ACSD-66084 para corregir el problema de Adobe Commerce en el que row_total_incl_tax devuelve un valor residual cercano a cero en lugar de 0,00 para los artículos con descuento completo en la respuesta de API del pedido.
feature: Orders, REST, Taxes, Payments, Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 421c6fe6-b6b1-4f33-acb6-fbd4306bcc4c
source-git-commit: 951738a4c671ed6fcc47b2a928d2110c78763d26
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# ACSD-66084: `row_total_incl_tax` devuelve casi cero en lugar de 0,00 para elementos con descuento completo en la API de pedidos

El parche ACSD-66084 corrige el problema en el que `row_total_incl_tax` se devuelve como un valor residual cercano a cero en la respuesta de API de pedido en lugar de 0,00 para los artículos con descuento completo. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. El ID del parche es ACSD-66084. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se devuelve `row_total_incl_tax` como un valor residual cercano a cero en la respuesta de API de pedidos en lugar de 0,00 para los artículos con descuento total.

<u>Pasos a seguir</u>:

1. Crea un producto con un precio y un precio especial. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > Haga clic en **[!UICONTROL Add Product]** > establezca **[!UICONTROL Price]** en $25 y **[!UICONTROL Special Price]** en $16.99 en **[!UICONTROL Advanced Pricing]**.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Taxes]** > **[!UICONTROL Tax Zones and Rates]** y agregue una tasa del 20%. A continuación, vaya a **[!UICONTROL Tax Rules]**, cree una regla y asígnela
   **[!UICONTROL Taxable Goods]** como clase de impuestos del producto.
1. Cree una regla de ventas con un descuento del 100% y un cupón. Vaya a **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** y agregue una regla con un descuento del 100%. Después, use **[!UICONTROL Specific Coupon]** e introduzca su código.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > y configure las opciones de impuestos.
1. Habilitar el envío gratuito. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL Free Shipping]**. Establezca **[!UICONTROL Enabled]** en **[!UICONTROL Yes]** y ajuste la configuración.
1. Vaya a la página del producto y seleccione **[!UICONTROL Add to Cart]**. Vaya al carro de compras y aplique el código de cupón.
1. Realice el pedido con la zona fiscal aplicable.
1. Genere un token de administrador (API) mediante la API de REST.
1. Recupere detalles del pedido mediante la API de REST.
1. Compruebe `row_total_incl_tax` en la respuesta.

<u>Resultados esperados</u>:

`row_total_incl_tax` debe devolver un valor apropiado para la moneda como `0.00` cuando el artículo esté totalmente descontado.

<u>Resultados reales</u>:

`row_total_incl_tax` devuelve un valor de punto flotante cercano a cero como `3.5527136788005e-15`, que no es apropiado para la visualización de moneda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
