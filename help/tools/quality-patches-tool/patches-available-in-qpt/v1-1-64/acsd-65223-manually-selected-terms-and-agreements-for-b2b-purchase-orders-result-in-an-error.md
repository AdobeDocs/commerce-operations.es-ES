---
title: 'ACSD-65223: Las condiciones y los acuerdos seleccionados manualmente para los pedidos de compra B2B dan como resultado un error'
description: Aplique el parche ACSD-65223 para solucionar el problema de Adobe Commerce donde los pedidos creados con [!UICONTROL Purchase Orders] no se pueden completar con métodos de pago en línea como tarjetas de crédito cuando se requieren términos y condiciones para el cierre de compra.
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 5a5d0774-3801-4688-86bd-58a390394cc0
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
source-wordcount: '457'
ht-degree: 0%
---
# ACSD-65223: Las condiciones y los acuerdos seleccionados manualmente para los pedidos de compra B2B dan como resultado un error

El parche ACSD-65223 corrige el problema en el que los pedidos creados con **[!UICONTROL Purchase Orders]** no se pueden completar con métodos de pago en línea como tarjetas de crédito cuando se requieren términos y condiciones para el cierre de compra. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. El ID del parche es ACSD-65223.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) B2B 1.5.1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) B2B 1.5.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Si se requieren términos y condiciones para realizar un pedido y está intentando finalizar un pedido creado con [!UICONTROL Purchase Orders], el pedido no se puede realizar mediante métodos de pago en línea como tarjetas de crédito.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** y elija **[!UICONTROL B2B Features]**.
1. Establezca **[!UICONTROL Enable Company]** y **[!UICONTROL Enable Purchase Orders]** en *Sí*.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Terms and Conditions]** y cree una nueva condición. Establezca **[!UICONTROL Applied]** en *[!UICONTROL Manually]*.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** y establezca **[!UICONTROL Enable Terms and Conditions]** en *Sí*.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment Methods]** y configure [!DNL Braintree].
1. En la tienda, cree una compañía.
1. En el administrador, vaya a **[!UICONTROL Customers]** > **[!UICONTROL Companies]**.
1. Apruebe la empresa y permita **[!UICONTROL Purchase Orders]**.
1. En el front-end, inicie sesión en la cuenta.
1. Agregar un elemento al carro de compras.
1. Realizar un pedido con **[!UICONTROL Purchase Order]**.
1. En el panel del cliente, haga clic en la ficha **[!UICONTROL Purchase Orders]**.
1. Cree un pedido a partir del nuevo pedido de compra. A continuación, selecciona la tarjeta de crédito como forma de pago.
1. Acepto los términos y condiciones.
1. Realice el pedido.

<u>Resultados esperados</u>:

Puede realizar un pedido utilizando un método de pago en línea en pedidos de compra aprobados cuando se requieran los términos y condiciones para el cierre de compra.

<u>Resultados reales</u>:

No puedes hacer un pedido usando un método de pago en línea en pedidos de compra aprobados cuando se requieren términos y condiciones para el pago.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
