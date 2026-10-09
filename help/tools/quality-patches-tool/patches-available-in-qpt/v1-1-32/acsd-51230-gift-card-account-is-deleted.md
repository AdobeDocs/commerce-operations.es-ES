---
title: 'ACSD-51230: se elimina la cuenta de la tarjeta regalo'
description: Aplique el parche ACSD-51230 para corregir el problema de Adobe Commerce en el que la cuenta de tarjeta de regalo se elimina cuando se procesa el reembolso parcial de un producto simple de un pedido.
feature: Customer Service, Gift, Marketing Tools
role: Admin
exl-id: a4aed574-3908-42e0-ac32-911f61b44995
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%
---
# ACSD-51230: se elimina la cuenta de la tarjeta regalo

El parche ACSD-51230 corrige el problema en el que la cuenta de la tarjeta regalo se elimina cuando el reembolso parcial de un producto simple se procesa a partir de un pedido. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.32. El ID del parche es ACSD-51230. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cuenta de tarjeta regalo se elimina cuando el reembolso parcial de un producto simple se procesa desde un pedido.

<u>Pasos a seguir</u>:

1. Crea un pedido con una *tarjeta regalo* y un *producto sencillo* (por ejemplo, *agrega: SKU: GI000XX000XXX, SKU: PC046CP042076*) - (cualquier método de pago y envío funciona).
1. Facturar el pedido.
1. Ir a **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Se crea una cuenta para la tarjeta regalo.
1. Ahora vaya a **[!UICONTROL Order]** y cree un(a) **[!UICONTROL Credit Memo]**.
1. Cambie la cantidad de la *tarjeta regalo* a 0 y actualícela. Esto creará un reembolso parcial por *producto simple*.
1. Haga clic en **[!UICONTROL Refund]**.
1. Ahora actualice **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Se elimina la cuenta recién creada.

<u>Resultados esperados</u>

La cuenta de la tarjeta regalo está disponible para su uso, ya que el reembolso no se creó para la tarjeta regalo.

<u>Resultados reales</u>

La cuenta de la tarjeta regalo se elimina y la tarjeta regalo no se devuelve.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
