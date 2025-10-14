---
title: 'ACSD-54989: el administrador de la compañía no puede realizar pedidos cuando [!UICONTROL Enable Purchase Orders] se establece en Yes y [!UICONTROL Purchase Order] se establece en No'
description: Aplique el parche ACSD-54989 para solucionar el problema de Adobe Commerce en el que el administrador de la empresa no puede realizar pedidos si [!UICONTROL Enable Purchase Orders] está establecido en Sí y [!UICONTROL Purchase Order] en No.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: 13830361-dd0c-486f-b07f-34280a17ab76
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-54989: el administrador de la compañía no puede ordenar cuando *[!UICONTROL Enable Purchase Orders]* se establece en *Yes* y *[!UICONTROL Purchase Order]* se establece en *No*

El parche ACSD-54989 corrige el problema en el que los pedidos no se pueden realizar si **[!UICONTROL Enable Purchase Orders]** se establece en *Yes* y **[!UICONTROL Purchase Order]** se establece en *No*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40. El ID del parche es ACSD-54989. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los administradores de la compañía no pueden realizar pedidos cuando **[!UICONTROL Enable Purchase Orders]** está establecido en *Sí* y **Pedido de compra** establecido en *No*.

<u>Requisitos previos</u>:

Instale [!DNL B2B] módulos.

<u>Pasos a seguir</u>:

1. Habilitar la compañía y dejar [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *No*.
1. Cree un producto simple con un precio de 100.
1. Cree una nueva compañía a través de Admin.
1. Establezca [!UICONTROL **Habilitar pedidos de compra**] en *Sí*.
1. Inicie sesión como administrador de la empresa en la tienda.
1. Añadir el producto simple creado al carro de compras.
1. Continúe con la página de cierre de compra y haga clic en **[!UICONTROL Place Order]** para completar la compra.

<u>Resultados esperados</u>:

Puede realizar un pedido correctamente.

<u>Resultados reales</u>:

La página **[!UICONTROL My Account]** se abre y no se realiza el pedido.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
