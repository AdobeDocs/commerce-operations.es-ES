---
title: 'ACSD-61133: "sales_clean_quote" cron elimina las ofertas de pedidos de compra no aprobados'
description: Aplique el parche ACSD-61133 para corregir el problema de Adobe Commerce en el que el cron sales_clean_quote elimina las ofertas de pedidos de compra no aprobados.
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 06979d4b-08ea-40fe-a211-3d950c9afb47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-61133: `sales_clean_quotes` cron elimina las ofertas de pedidos de compra no aprobados

El parche ACSD-61133 corrige el problema en el que el cron `sales_clean_quotes` elimina las cotizaciones de pedidos de compra no aprobados. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.53. El ID del parche es ACSD-61133. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4-p5 - 2.4.4-p11, 2.4.5-p4 - 2.4.5-p10 y 2.4.6-p2 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

`sales_clean_quotes` cron elimina las ofertas de los pedidos de compra no aprobados. El *[pedido de compra B2B]* no se puede convertir en el pedido de la oferta asociado con el pedido comprado, ya que el cron lo elimina.

<u>Requisitos previos</u>:

Los módulos de Adobe Commerce [!UICONTROL B2B] están instalados y habilitados.

<u>Pasos a seguir</u>:

1. Habilitar la funcionalidad *[!UICONTROL B2B Purchase Order]*.
1. Cree una empresa.
1. Crear un *[!UICONTROL Purchase Order]*.
1. Espere hasta que la cotización caduque y sea eliminada por el cron. El período de caducidad de la oferta puede establecerse con **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]** > **[!UICONTROL Default Expiration Period configuration]**.
1. Convertir *[!UICONTROL Purchase Order]* al orden mediante *[!UICONTROL My Purchase Order in Customer Dashboard]* o con la mutación [!DNL GraphQL] `placeOrderForPurchaseOrder`.

<u>Resultados esperados</u>:

La oferta asociada con el activo *[!UICONTROL Purchase Order]* no se elimina porque la oferta ha caducado. El pedido se realizó correctamente en la tienda o a través de [!DNL GraphQL].

<u>Resultados reales</u>:

El pedido no se realiza y se muestra un error en la tienda o se devuelve en la respuesta [!DNL GraphQL].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
