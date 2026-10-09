---
title: 'ACSD-57315: se crea una nueva transacción en [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón de recuperación'
description: Aplique el parche ACSD-57315 para corregir el problema de Adobe Commerce en el que se crea una nueva transacción en [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón de recuperación en la pantalla Ver transacción en [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
exl-id: 1fb8a5af-fda1-4c24-859d-d45424bde12f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
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
source-wordcount: '403'
ht-degree: 0%
---
# ACSD-57315: se crea una nueva transacción en [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón de recuperación

La revisión ACSD-57315 corrige el problema en el que se crea una nueva transacción en [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón de recuperación en la pantalla Ver transacción en [!UICONTROL Admin]. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.48. El ID del parche es ACSD-57315. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se crea una nueva transacción en [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón Recuperar en la pantalla Ver transacción en [!UICONTROL Admin].

<u>Pasos a seguir</u>:

1. Configurar [!DNL PayPal Payflow Pro].
1. Establezca el método de transacción en *[!UICONTROL Sale]*.
1. Haz un pedido con *tarjeta de crédito*.
1. Abra la transacción de [!UICONTROL Admin].
1. Haga clic en el botón **[!UICONTROL Fetch]**.
1. Compruebe la cuenta de [!DNL PayPal] para ver las transacciones relacionadas con el pedido realizado.

<u>Resultados esperados</u>:

No se crea una nueva transacción de pago.

<u>Resultados reales</u>:

Se crea una nueva transacción de pago para un pedido que ya se ha pagado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
