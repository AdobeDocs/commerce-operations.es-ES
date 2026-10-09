---
title: 'ACSD-48362: se utiliza la dirección de envío predeterminada en lugar de una nueva.'
description: Aplique el parche ACSD-48362 para solucionar el problema de Adobe Commerce en el que se utiliza la dirección de envío predeterminada en lugar de una nueva al realizar un pedido con una oferta negociable.
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
exl-id: 6f0717a6-1e29-4059-9640-5b92586c36e4
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%
---
# ACSD-48362: se utiliza la dirección de envío predeterminada en lugar de una nueva

El parche ACSD-48362 corrige el problema en el que se utiliza la dirección de envío predeterminada en lugar de la dirección recién agregada al realizar un pedido utilizando una cotización negociable. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.27. El ID del parche es ACSD-48362. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se utiliza la dirección de envío predeterminada en lugar de la dirección de envío recién agregada al realizar un pedido con una oferta negociable.

<u>Pasos a seguir</u>:

1. Para habilitar el presupuesto B2B, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**.
1. Inicie sesión como usuario de la empresa.
1. Añadir un producto al carro de compras.
1. Vaya a la página del carro de compras y solicite un presupuesto.
1. Vaya a la página **[!UICONTROL My Quotes]** del cliente y seleccione la oferta que acaba de crear.
1. Vaya a la sección **[!UICONTROL Shipping Information]** de la página del presupuesto del cliente.
   * Haga clic en **[!UICONTROL Add New Address]**, rellene el formulario y guarde la dirección (no seleccione **[!UICONTROL Use as my default billing address]** ni **[!UICONTROL Use as my default shipping address]**).
1. Haga clic en **[!UICONTROL Send for Review]** en la página de presupuesto del cliente.
1. Vaya al Administrador de Adobe Commerce como usuario administrador, abra la oferta que acaba de crear y haga clic en **[!UICONTROL Send]**.
1. Ahora ve a la página de presupuesto del cliente, actualiza la página y haz clic en **[!UICONTROL Proceed to Checkout]**.
1. En la página de pago y envío, los datos muestran la dirección de envío predeterminada incluso cuando se selecciona la nueva dirección de envío.
1. Haga clic en **[!UICONTROL Continue]** y realice el pedido.

<u>Resultados esperados</u>:

El pedido debe utilizar la nueva dirección sin volver a seleccionar la dirección de envío predeterminada en la página de cierre de compra.

<u>Resultados reales</u>:

El pedido se realiza con la dirección de envío predeterminada.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube. 

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
