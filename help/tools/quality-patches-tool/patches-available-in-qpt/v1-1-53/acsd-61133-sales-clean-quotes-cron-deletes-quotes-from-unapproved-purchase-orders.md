---
title: 'ACSD-61133: "sales_clean_quote" cron elimina las ofertas de pedidos de compra no aprobados'
description: Aplique el parche ACSD-61133 para corregir el problema de Adobe Commerce en el que el cron sales_clean_quote elimina las ofertas de pedidos de compra no aprobados.
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 06979d4b-08ea-40fe-a211-3d950c9afb47
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
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
source-wordcount: '381'
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
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
