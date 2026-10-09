---
title: 'ACSD-61134: [!UICONTROL Braintree Vault] método de pago deseleccionado automáticamente en el flujo de trabajo de cierre de compra'
description: Aplique el parche ACSD-61134 para resolver el problema de Adobe Commerce en el que el método de pago *[!UICONTROL Braintree Vault]* se anula automáticamente en el flujo de trabajo de cierre de compra cuando un comprador actualiza su dirección de facturación anulando la selección de la casilla de verificación *[!UICONTROL My billing and shipping address are the same]*.
feature: Checkout
role: Admin, Developer
exl-id: 8aad34e2-89ef-460c-8921-91098bd1645b
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
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%
---
# ACSD-61134: *[!UICONTROL Braintree Vault]* método de pago deseleccionado automáticamente en el flujo de trabajo de cierre de compra

El parche ACSD-61134 corrige el problema en el que el método de pago *[!UICONTROL Braintree Vault]* se anula automáticamente de la selección en el flujo de trabajo de cierre de compra cuando un comprador actualiza su dirección de facturación anulando la selección de la casilla de verificación *[!UICONTROL My billing and shipping address are the same]*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. El ID del parche es ACSD-61134. Tenga en cuenta que este problema está programado para solucionarse en Adobe Commerce 2.4.7-beta1.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6-p7

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El método de pago *[!UICONTROL Braintree Vault]* se deselecciona automáticamente en el flujo de trabajo de cierre de compra.

<u>Pasos a seguir</u>:

1. Configure el método de pago *[!DNL Braintree]* con *[!UICONTROL Vault]* habilitado.
1. Cierre la compra y guarde una tarjeta en *[!UICONTROL Vault]*.
1. Cierre otro producto.
1. En la página *[!UICONTROL Shipping]*, agregue una nueva dirección de envío para que tenga dos direcciones que seleccionar.
1. En la página *[!UICONTROL Payment]*, seleccione la forma de pago y haga clic en **[!UICONTROL My billing and shipping addresses are the same]**.

<u>Resultados esperados</u>:

El método de pago seleccionado permanece seleccionado.

<u>Resultados reales</u>:

El método de pago seleccionado está desmarcado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
