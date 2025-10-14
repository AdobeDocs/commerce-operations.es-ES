---
title: 'ACSD-48044: la aplicación de varias tarjetas regalo evita que se realicen pedidos'
description: Aplique el parche ACSD-48044 para solucionar el problema de Adobe Commerce cuando la aplicación de varias tarjetas regalo a un único pedido con envío múltiple impide que se realicen pedidos.
feature: Admin Workspace, Gift, Orders
role: Admin
exl-id: c7b72b1f-2f1b-4445-b842-5847d05d5ae9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-48044: la aplicación de varias tarjetas regalo evita que se realicen pedidos

El parche ACSD-48044 soluciona el problema de que la aplicación de varias tarjetas regalo a un único pedido con envío múltiple impide que se realicen pedidos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25. El ID del parche es ACSD-48044. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La aplicación de varias tarjetas regalo a un único pedido con envío múltiple impide que se realicen pedidos.

<u>Pasos a seguir</u>:

1. Instale una versión limpia de Adobe Commerce.
1. Cree un producto simple con un precio de 100 $ y otro producto simple con un precio de 10 $.
1. Inicie sesión en [!UICONTROL Admin panel] y cree dos tarjetas regalo.

   * 02KB8M0H0GRD = 50 $
   * 00GXM6SUGBLW = 25 $

1. Cree un cliente con dos direcciones.
1. Agregue dos productos al carro de compras.

   * Primero agregue el producto de 10 $ y luego el producto de 100 $. El problema no se puede reproducir si primero se agrega el producto de 100 $.

1. Vaya al carro de compras y añada las dos tarjetas regalo que ha creado.
1. Haga clic en **[!UICONTROL Ship to Multiple Addresses]** en la página del carro de compras.
1. Asigne cada producto a una dirección diferente.
1. Vaya a la página **[!UICONTROL Shipping information]**.
1. Vaya a la página **[!UICONTROL Billing information]**.
1. Vaya a la página **[!UICONTROL Review Your Order]**, donde podrá ver el problema.
1. Intente realizar el pedido.

<u>Resultados esperados</u>:

* Las tarjetas de regalo se aplican correctamente al importe total.
* Se realizan los pedidos.

<u>Resultados reales</u>:

Las cantidades de la tarjeta regalo se mezclan con un error *&quot;Corrija el código de la tarjeta regalo&quot;.* al realizar el pedido.

* Primer producto:

   * Retire la tarjeta regalo (00GXM6SUGBLW) - $15.00
   * Retire la tarjeta regalo (02KB8M0H0GRD) - $0.00

* Segundo producto:

   * Retire la tarjeta regalo (00GXM6SUGBLW) - $25.00
   * Retire la tarjeta regalo (02KB8M0H0GRD) - $35.00

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
