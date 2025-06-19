---
title: 'ACSD-55610: el pedido parcialmente cancelado tiene un importe de descuento incorrecto'
description: Aplique el parche ACSD-55610 para solucionar el problema de Adobe Commerce en el que un pedido parcialmente cancelado tiene un importe de descuento incorrecto.
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: b7b94c9d-e027-4601-837b-d70b7ff8bd2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55610: el pedido parcialmente cancelado tiene un importe de descuento incorrecto

El parche ACSD-55610 soluciona el problema de los pedidos parcialmente cancelados que tienen un importe de descuento incorrecto. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.43. El ID del parche es ACSD-55610. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un pedido parcialmente cancelado tiene un importe de descuento incorrecto.

<u>Pasos a seguir</u>:

1. Crear una regla de precios del carro de compras.

   * *[!UICONTROL Rule Name]*: *Rebajas de invierno*
   * *[!UICONTROL Active]* = *Sí*
   * *[!UICONTROL Websites]* = *Sitio web principal*
   * Seleccione todos los grupos de clientes.
   * Seleccione un cupón específico.
   * *[!UICONTROL Coupon Code]*: *INVIERNO10*
   * *[!UICONTROL Conditions]*: *[!UICONTROL If ALL of these conditions are TRUE]*: *Subtotal(Excl. Tax) es igual o mayor que 75*
   * Aplicar *[!UICONTROL Percent of product price discount]*.
   * *[!UICONTROL Discount Amount]*: *10*
   * *[!UICONTROL Discard subsequent rules]*: *Sí*

1. Cree tres productos con los precios establecidos en 100.
1. Agregue los tres productos al carro de compras.
1. Aplique el cupón.
1. Realice el pedido.
1. Facturar un artículo del pedido y enviarlo.
1. Cancelar los otros dos elementos.
1. Compruebe la columna `base_discount_canceled`.

<u>Resultados esperados</u>:

La cantidad de descuento en `base_discount_cancelled` se refleja correctamente.

<u>Resultados reales</u>:

`base_discount_cancelled` no es correcto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
