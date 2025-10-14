---
title: 'ACSD-49042: El producto con un pedido pendiente infinito no se puede pedir desde la tienda'
description: Aplique el parche ACSD-49042 para corregir el problema de Adobe Commerce en el que un producto con un pedido pendiente infinito no se puede pedir desde la tienda.
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
exl-id: b94d06c0-806a-40be-bcd4-d6b8e5e474c3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-49042: El producto con un pedido pendiente infinito no se puede pedir desde la tienda

El parche ACSD-49042 soluciona el problema de que un producto con un pedido pendiente infinito no se puede pedir desde la tienda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27. El ID del parche es ACSD-49042. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El error se produce cuando un producto con un pedido pendiente infinito no se puede pedir desde la tienda.

<u>Pasos a seguir</u>:

1. Establezca las siguientes opciones de configuración:
   * **[!UICONTROL Display Out of Stock Products]** se estableció en *[!UICONTROL Yes]*.
   * **[!UICONTROL Backorders]** se estableció en *[!UICONTROL Allow Qty Below 0]*.
1. Agregar **[!DNL custom stock]** y **[!DNL custom source]** nuevos.
1. Asigne un producto a **[!DNL custom source]** y asegúrese de que haya un número de inventario establecido para él (por ejemplo: *10*).
1. En la página de edición del producto, abra **[!UICONTROL Advanced Inventory]**. Establezca **[!UICONTROL minimum quantity]** en el carro de compras (por ejemplo: *160*). La cantidad debe estar por encima del inventario.
1. Vaya a la tienda y compre un producto para crear una reserva.
1. Cambiar **[!UICONTROL product quantity]** a *0*. El punto crítico es guardar el producto de **[!DNL Admin panel]** cuando hay una reserva.
1. Abra **[!UICONTROL product page]** en la tienda e intente agregar el producto al carro de compras.

<u>Resultados esperados</u>:

Es posible agregar el producto al carro de compras porque se permiten pedidos pendientes de una cantidad inferior a *0*.

<u>Resultados reales</u>:

Se muestra que el producto está agotado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
