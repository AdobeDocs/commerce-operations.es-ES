---
title: 'ACSD-62118: la tabla "sales_order_tax_item" no se ha actualizado completamente para los pedidos B2B realizados con el método [!UICONTROL Purchase Order]'
description: Aplique el parche ACSD-62118 para corregir el problema de Adobe Commerce en el que la tabla sales_order_tax_item no se actualiza completamente cuando los pedidos B2B se realizan mediante el método [!UICONTROL Purchase Order].
feature: Purchase Orders, B2B
role: Admin, Developer
source-git-commit: 5812b90fe07a084a1d3487784d0f36a2b7958286
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---


# ACSD-62118: la tabla `sales_order_tax_item` no se ha actualizado completamente para los pedidos B2B realizados con el método [!UICONTROL Purchase Order]

El parche ACSD-62118 corrige el problema en el que la tabla `sales_order_tax_item` no se actualiza completamente cuando se realiza un pedido B2B utilizando el método *[!UICONTROL Purchase Order]*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. El ID del parche es ACSD-62118. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando se realizan pedidos B2B utilizando el método *[!UICONTROL Purchase Order]*, la tabla `sales_order_tax_item` no se actualiza completamente. Este problema afecta a los cálculos de impuestos y al procesamiento de pedidos. Específicamente, la matriz `applied_taxes` está vacía al consultar el pedido a través de la API, y tanto `tax_item_amount` como `tax_item_percent` son NULL.

<u>Pasos a seguir</u>:

1. Agregar reglas fiscales para **[!UICONTROL Product]** y **[!UICONTROL Shipping]**.
1. Habilite el método **[!UICONTROL Purchase Order]** en la configuración de la compañía.
1. Inicie sesión como usuario administrador de la empresa.
1. Colocar un **[!UICONTROL Purchase Order]** mediante un método de pago sin conexión.
1. Una vez que [!UICONTROL Purchase Order] se apruebe automáticamente y se convierta en un pedido, compruebe los datos de impuestos en la tabla `sales_order_tax_item` y a través de la API de REST.

<u>Resultados esperados</u>:

* La tabla `sales_order_tax_item` debe contener `tax_item` datos.
* La matriz `applied_taxes` debe mostrar la información fiscal correcta en la respuesta de API para los pedidos de compra, de forma similar a otros métodos de pago (por ejemplo, cheque o giro postal).

<u>Resultados reales</u>:

* La tabla `sales_order_tax_item` no contiene datos de `tax_item`.
* Las matrices `applied_taxes` y `item_applied_taxes` están vacías en la respuesta de API para *[!UICONTROL Purchase Order]*.
* No se muestran datos de impuestos al usar el método de pago *[!UICONTROL Purchase Order]*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
