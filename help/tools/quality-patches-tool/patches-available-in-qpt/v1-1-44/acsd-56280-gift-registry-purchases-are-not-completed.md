---
title: 'ACSD-56280: las compras en el registro de regalos no se han completado'
description: Aplique el parche ACSD-56280 para corregir el problema de Adobe Commerce en el que las compras del registro de regalos no se hayan completado
feature: Checkout
role: Admin
exl-id: a79f789f-999f-4d11-b7ee-2c065b681efb
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%
---
# ACSD-56280: las compras en el registro de regalos no se han completado

>[!NOTE]
>
>Este parche se reemplazó por [ACSD-63283](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/acsd-63283-resolving-gift-registry-email-and-order-placement-issues-in-adobe-commerce.md).

El parche ACSD-56280 corrige el problema en el que las compras del registro de regalos no se completan. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.44. El ID del parche es ACSD-56280. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las compras del registro de regalos no se han completado.

<u>Pasos a seguir</u>:

1. Inicie sesión como cliente y agregue **[!UICONTROL product]** al registro de regalos.
1. Comparta el vínculo del registro de regalos.
1. Abra el vínculo del registro de regalos en otra ventana del explorador o de incógnito.
1. Agregue la cantidad y agregue los artículos al carro de compras.
1. Vaya a **[!UICONTROL Checkout Page]** y seleccione **[!UICONTROL shipping method]** (ya que la dirección de envío está seleccionada, proporcionada por el solicitante de registro).
1. Seleccione el método de pago.
1. Haga clic en el botón Realizar pedido.

<u>Resultados esperados</u>:

Se debe realizar el pedido.

<u>Resultados reales</u>:

El pedido no se realizó y se muestra el error `Call to a member function getUpdatedQty() on null`.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
