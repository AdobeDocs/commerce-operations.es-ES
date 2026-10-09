---
title: 'ACSD-60234: [!DNL PayPal] muestra una cantidad incorrecta cuando se aplica el descuento'
description: Aplique el parche ACSD-60234 para solucionar el problema de Adobe Commerce donde [!DNL PayPal] muestra una cantidad incorrecta cuando el descuento se aplica mediante el método de pago.
feature: Products, Configuration
role: Admin, Developer
exl-id: 2ce7bde5-02a4-4989-80d6-ab1be0ca5fe9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
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
source-wordcount: '423'
ht-degree: 0%
---
# ACSD-60234: [!DNL PayPal] muestra una cantidad incorrecta cuando se aplica el descuento

El parche ACSD-60234 corrige el problema en el cual [!DNL PayPal] muestra una cantidad incorrecta cuando el descuento se aplica a través del método de pago. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.51. El ID del parche es ACSD-60234. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!DNL PayPal] muestra un importe incorrecto cuando el descuento se aplica a través del método de pago.

<u>Pasos a seguir</u>:

1. Configurar *[!DNL PayPal Express]* en **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment methods]** > **[!DNL PayPal]** > **[!UICONTROL Express checkout]**.
   * [!UICONTROL Enable In-Context Checkout] puede ser [!UICONTROL Yes] o [!UICONTROL NO], el problema se reproduce en ambos casos.
1. Crear un *[!UICONTROL Cart Rule]* en **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add New Rule]**.
   * Condición: si todas estas condiciones son verdaderas: *[!UICONTROL Payment Method]* es *[!DNL PayPal Express Checkout]*.
   * Acciones: cualquier acción.
1. Cree un producto.
1. Vaya a la tienda, agregue el producto al carro y, a continuación, vaya al paso **[!UICONTROL Payment Method]** del cierre de compra.
1. Asegúrese de seleccionar *[!DNL PayPal Express]* y de validar que el descuento se aplica correctamente.
1. Haga clic en el botón **[!DNL PayPal]**.
1. Inicie sesión y observe el contenido de la ventana emergente.

<u>Resultados esperados</u>:

La cantidad que se va a pagar pasada a [!DNL PayPal] incluye el descuento tal como está en el carro de compras.

<u>Resultados reales</u>:

El importe total a pagar no incluye el descuento.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
