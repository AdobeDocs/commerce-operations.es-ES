---
title: 'ACSD-51204: El producto no vuelve a estar disponible después de crear la nota de crédito'
description: Aplique el parche ACSD-51204 para solucionar el problema de Adobe Commerce en el que el producto no vuelve a estar disponible después de crear la nota de crédito.
feature: Orders, Products, Returns
role: Admin
exl-id: a4dba28c-c239-4812-8b3a-ce0493f9b1aa
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%
---
# ACSD-51204: El producto no vuelve a estar disponible después de crear la nota de crédito

El parche ACSD-51204 corrige el problema en el que el producto no vuelve a estar disponible después de crear la nota de crédito. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32. El ID del parche es ACSD-51204. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El producto agotado no vuelve a estar disponible después de crear la nota de crédito.

<u>Pasos a seguir</u>:

1. Instale **[!UICONTROL Adobe Commerce]** y habilite **[!UICONTROL Inventory Management Module]** solo con *origen* y *existencias* predeterminados.
1. Agregar un(a) **[!UICONTROL new product]** con una cantidad de *10*.
1. Asigne el producto a **[!UICONTROL default stock]**.
1. En la Tienda, agrega el producto al carro y realiza un pedido de toda una cantidad disponible 10.
1. En el panel de administración, genere una *factura* y un *envío* para el pedido.
1. Cree un(a) **[!UICONTROL Credit Memo]** con la casilla de verificación *volver al inventario* seleccionada(a) para todos los elementos.
1. Compruebe **[!UICONTROL Salable Quantity]** del producto en el administrador.

<u>Resultados esperados</u>:

La cantidad vendible del producto tiene que volver a *10*.

<u>Resultados reales</u>:

La cantidad vendible del producto se ha dejado como *0*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
