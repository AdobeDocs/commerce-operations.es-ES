---
title: '49843 ACSD: el vínculo de descarga de producto no está disponible después de facturarse automáticamente con [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'
description: Aplique el parche ACSD-49843 para solucionar el problema de Adobe Commerce en el que el vínculo de descarga de productos no está disponible después de que un método de pago en línea factura automáticamente el artículo pedido cuando [!UICONTROL Payment Action] se establece en [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: e990b550-fb32-48d2-9c39-2176d7ab34c9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
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
source-wordcount: '510'
ht-degree: 0%
---
# ACSD-49843: el vínculo de descarga de producto no está disponible después de facturarse automáticamente con [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

El parche ACSD-49843 corrige el problema en el que el vínculo de descarga del producto no está disponible después de que un método de pago en línea haya facturado automáticamente el elemento solicitado cuando [!UICONTROL Payment Action] está establecido en [!UICONTROL Intent Sale]. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.37. El ID del parche es ACSD-49843. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El vínculo de descarga de productos no está disponible después de que un método de pago en línea haya facturado automáticamente el artículo pedido cuando [!UICONTROL Payment Action] está establecido en [!UICONTROL Intent Sale].

<u>Pasos a seguir</u>:

1. Inicie sesión en Adobe Commerce Admin y vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * En la lista desplegable [!UICONTROL Payment Action], seleccione **[!UICONTROL Intent Sale]** y establezca *[!UICONTROL Enable Card Payments]* en *Sí*.

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]** y asegúrese de que está establecido en *&quot;Facturado&quot;*.
1. En la tienda, inicie sesión como cliente.

   * Añada cualquier producto descargable y un producto simple al carro de compras.
   * Use [!DNL Braintree Pay] para hacer el pedido con la opción de tarjeta.

1. Vaya a **[!UICONTROL My Orders]** y compruebe que la factura se crea automáticamente para el pedido y que ambos estados de artículo son *&quot;Facturado&quot;*.
1. Vaya a **[!UICONTROL My Downloadable Products]** y observe que el vínculo de descarga aún no está disponible.
1. En el Administrador, vaya a ese pedido y cree un envío para él.
1. En la tienda, vaya a **[!UICONTROL My Downloadable Products]** y observe que el vínculo de descarga ya está disponible.

<u>Resultados esperados</u>:

El vínculo de descarga está disponible cuando el estado del producto descargable es *&quot;Facturado&quot;*.

<u>Resultados reales</u>:

El vínculo de descarga no está disponible aunque el estado del producto descargable indique *&quot;Facturado&quot;*. Solo está disponible después de crear un envío para el producto físico.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
